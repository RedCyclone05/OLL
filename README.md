# Proyecto F2L

## Descripción

Este proyecto está diseñado para procesar imágenes relacionadas con el método F2L (First Two Layers) del cubo Rubik y generar un documento PDF con las imágenes y detalles relevantes. Ademas se genera un Deck de Flashcards de Anki por cada grupo. El proceso incluye:

1. **Descarga de Imágenes**: Descarga imágenes desde enlaces generados a partir de un archivo CSV, llamado `DataBase.csv`.
2. **Procesamiento de Imágenes**: Aplica un filtro de relleno a las imágenes para resaltar áreas específicas.
3. **Generar el algoritmo Set Up**: Añade una nueva columna al archivo CSV llamado `DataBase.csv` la cual contiene el algoritmo Set Up, cuya función es plantear el caso a resolver.
4. **Generar los Triggers**: Modifica el archivo CSV llamado `DataBase.csv`, para ello analiza todas las columnas en la cual haya presente un algoritmo y lo divide en pequeños grupos de movimientos llamados Triggers. 
5. **Generación de PDF**: Crea un documento PDF que incluye las imágenes procesadas, los algoritmos provenientes de un archivo CSV llamado `DataBase.csv`, con un formato estético y organizado.
6. **Dividir la base de datos por Grupo**: Divide la base de datos de un archivo CSV llamado `DataBase.csv` en  nuevas bases de datos de acuerdo al grupo que pertenecen. Además modifica el orden, para que el Slot Back Right aparezca antes que el Slot Back Left, esto por facilidad al aprendizaje.
7. **Genera Decks de Anki**: Genera un Deck de Anki por cada grupo seleccionado, le pregunta al usuario, el nombre del Deck y le pregunta que archivo CSV se necesita usar.

## Estructura del Proyecto

El proyecto consta de tres scripts principales:

1. **Descargar Imágenes** (`download_images.py`): Este script descarga imágenes desde enlaces especificados en un archivo CSV y las guarda en una carpeta local.

2. **Procesar Imágenes** (`process_images.py`): Abre las imágenes descargadas, aplica un filtro de relleno y guarda las imágenes procesadas en una carpeta específica.

3. **Generar el algoritmo SetUp para cada caso** (`set_up_generator.py`): Lee un archivo CSV con informacion sobre cada caso, luego genera un nuevo algoritmo el cual sirve para plantear el caso especifico y luego se le añade a la columna 10 del CSV original.

4. **Generar los Triggers**(`trigger_generator.py`): Modifica el archivo CSV, para ello analiza todas las columnas en la cual haya presente un algoritmo y lo divide en pequeños grupos de movimientos llamados Triggers. 

5. **Generar PDF** (`generate_pdf.py`): Lee un archivo CSV con información sobre las imágenes y genera un documento PDF que incluye las imágenes procesadas y detalles adicionales.


6. **Dividir la base de datos por Grupo** (`group_generator.py`): Lee un archivo CSV con información de cada caso y lo divide en nuevos archivos CSV separados por Grupo de casos, guarda todos estos archivos en una carpeta en especifico. Además modifica el orden de los slots, de modo que el BR aparezca antes que el BL.

7. **Generar Deck de Anki** (`anki_generator.py`): Pregunta al usuario que archivo CSV quiere que lea para generar el Deck de Anki, genera un Deck de Anki con los casos elegidos. En la parte frontal plantea el algoritmo para colocar el caso deseado, en la parte de atras se muestra la imagen del caso y debajo de ella se muestran los algoritmos para resolver dicho caso. 

## Requisitos

- Python 3.x
- Bibliotecas Python:
  - `Pillow`
  - `matplotlib`
  - `numpy`
  - `reportlab`
  - `shutil`
  - Anki

## Instrucciones de Uso

1. **Ejecutar Scripts**:
   - **Descargar Imágenes**: Ejecuta `download_images.py` para descargar las imágenes necesarias, se guardaran en la carpeta `preliminary_downloaded_images`.
   - **Procesar Imágenes**: Ejecuta `process_images.py` para procesar las imágenes descargadas ubicadas en la carpeta `preliminary_downloaded_images`, conforme las imagenes se procesan se guardaran en `processed_downloaded_images`. Una vez se ejecute el codigo, el usuario debera clickear en las regiones que desee ocultar, además, luego del procesamiento automatico, el codigo permite al usuario indicar que imagen en especifico desea procesar.
   - **Generar PDF**: Ejecuta `generate_pdf.py` para generar el documento PDF final.
   - **Generar algoritmo Set UP**: Ejecuta `set_up_generator.py` para añadir al archivo CSV `DataBase.csv` una columna que contenga un algoritmo Set Up para cada caso.
   - **Dividir la base de datos por Grupo** Ejecuta `group_generator.py` para dividir el archivo CSV `DataBase.csv` en nuevos archivos CSV separados por Grupo de casos, guarda todos estos archivos en la carpeta `Divided_CSV`.
   - **Generar Deck de Anki** Ejecuta `anki_generator.py` para generar automaticamente un Deck de Anki. El script pregunta al usuario el nombre del Deck y que archivo CSV quiere que lea para generar el Deck de Anki, genera un Deck de Anki con los casos elegidos. En la parte frontal plantea el algoritmo para colocar el caso deseado, en la parte de atras se muestra la imagen del caso y debajo de ella se muestran los algoritmos para resolver dicho caso. 

   ```bash
   python download_images.py
   python process_images.py
   python generate_pdf.py
   python set_up_generator.py
   python group_generator.py
   python anki_generator.py
    ```
2. **Usar Flashcards**:
    - **Instalar Anki** Si no tienes Anki instalado, descárgalo e instálalo desde [ankiweb.net](https://apps.ankiweb.net/)
    - **Instalar el Deck** Una vez hayas generado el Deck (`Nombre_elegido_por_el_usuario.apkg`), simplemente dale doble clic al archivo. Esto abrirá automáticamente Anki e importará el deck.
    - **Abrir Anki** Abre Anki y verás tu nuevo Deck en la lista de Decks. Selecciona el Deck para empezar a estudiar.
    - **Iniciar la Práctica** Al iniciar la práctica, aparecerá el algoritmo de Set Up en el anverso de la tarjeta (parte frontal), el cual deberás aplicar en el cubo Rubik. Presiona la barra espaciadora para ver la respuesta.
    - **Mostrar la Respuesta** Después de presionar la barra espaciadora, verás la imagen del caso y los algoritmos para resolverlo en el reverso de la tarjeta (parte trasera).
    - **Evaluar tu Conocimiento** Después de revisar la respuesta, Anki te preguntará si ya conoces el caso o si necesitas seguir practicándolo. Tendrás opciones como "Fácil", "Buena", "Difícil", o "Repetir". Selecciona la opción según tu nivel de confianza en ese caso. Se sincero, si no, no servira.
    - **Configurar el Número de Tarjetas por Día** Una vez termines tu sesión, puedes ajustar el número máximo de tarjetas que deseas repasar por día. Para hacerlo, selecciona tu Deck en la pantalla principal de Anki, haz clic en "Opciones" y ajusta el número de tarjetas nuevas y de repaso en la sección correspondiente.

    De esta forma, podrás mejorar tu conocimiento del método F2L mediante la repetición espaciada, asegurándote de dominar todos los casos a tu propio ritmo.


## Resultados:

1. Las imágenes procesadas se guardarán en la carpeta `processed_downloaded_images`.

2. El documento PDF generado se guardará como `F2L_cases.pdf`.

3. Los nuevos CSV divididos por grupo se guardaran en la carpeta `Divided_CSV`. Cada archivo se llamara `Nombre_de_su_categoria.csv` y además se creara una copia del archivo `DataBase.csv`

4. Los Decks de Anki se guardaran como `Nombre_elegido_por_el_usuario.apkg`.

