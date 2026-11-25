# EP.03.01 Streaming - Gustavo Adalid

Ejercicios de Spark Structured Streaming con una fuente socket (netcat).

| Notebook | Ejercicio |
|---|---|
| `Streaming2_Modos_de_Salida.ipynb` | Comparar los modos de salida `complete`, `update` y `append` |
| `Streaming3_Triggers.ipynb` | Trigger por intervalo de 1 minuto |

## Requisitos en Fedora

```bash
sudo dnf install -y java-17-openjdk-headless python3 python3-pip nmap-ncat
```

## Entorno de Python

```bash
git clone https://github.com/gustavoadalid1-debug/EP.03.01.-Streaming---GustavoAdalid.git
cd EP.03.01.-Streaming---GustavoAdalid
python3 -m venv venv
source venv/bin/activate
pip install pyspark jupyterlab
```

## Ejecución

Usa dos terminales.

Terminal 1, fuente de datos (déjala abierta):

```bash
nc -lk 9999
```

Terminal 2, Jupyter:

```bash
source venv/bin/activate
jupyter lab
```

Abre el notebook y ejecuta las celdas en orden. Los resultados de cada batch se muestran dentro del notebook con `mostrar()`.

Para enviar datos, escribe frases en la Terminal 1 y presiona Enter, por ejemplo:

```
Esta es la primera frase
Enviamos segunda linea primera
```

## Notas

- Ejecuta un notebook a la vez: ambos usan el puerto 9999. Al terminar uno, cierra su kernel.
- Ejecuta las celdas una por una; no uses *Run All*, porque los pasos con `nc` necesitan que tú envíes las frases.
- Si ves `Cannot call methods on a stopped SparkContext`, reinicia el kernel (Kernel > Restart) y ejecuta desde la primera celda.
- Si `nc` queda ocupado, ciérralo con `Ctrl+C` y vuelve a abrirlo.
