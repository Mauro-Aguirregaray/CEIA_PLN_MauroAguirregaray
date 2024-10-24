<img src="https://github.com/hernancontigiani/ceia_memorias_especializacion/raw/master/Figures/logoFIUBA.jpg" width="500" align="center">

# Procesamiento de Lenguaje Natural

Este repositorio pertenece a Mauro Aguirregaray, alumno de la 15a Cohorte de la Especialización en Inteligencia Artificial. Contiene los cinco desafíos realizados para la materia de Procesamiento de Lenguaje Natural. Los trabajos están presentados en Jupyter Notebooks, junto con imágenes que muestran los resultados de diferentes modelos de procesamiento de lenguaje, incrementando su complejidad progresivamente.

A continuación, se ofrece un resumen de cada desafío y sus respectivos resultados.

## Desafío 1

En esta primera experiencia, se trabajó con modelos básicos de procesamiento de texto. Se exploró la vectorización de documentos y palabras, y se evaluó la capacidad de comparación utilizando la *similaridad del coseno*. 

A pesar de la simplicidad del enfoque, los resultados fueron satisfactorios, particularmente en la predicción de la temática de los documentos, aplicando un preprocesamiento ligero de los datos y un modelo básico de *Naive Bayes*. Sin embargo, al aplicar esta metodología a palabras, los resultados no fueron tan alentadores, demostrando la necesidad de emplear modelos más complejos para capturar mejor las relaciones semánticas, lo cual se abordará en los siguientes desafíos.

## Desafío 2

En este desafío se aborda el tema anterior y se busca entrenar *embeddings* de palabras para comprobar si, de esta manera, logramos encontrar similitudes. Para este caso, se toma un tema de interés personal, que en mi caso es la [energía eólica](Desafio2/Wind_Energy_Handbook.pdf).

Aquí aprendimos a trabajar con archivos de texto genéricos, en particular, un libro científico en formato PDF, realizar el preprocesamiento necesario y entrenar los *embeddings*.

Los resultados obtenidos son, sin duda, mejores que los del Desafío 1, aunque las limitaciones de técnicas y de hardware siguen presentando problemas. A continuación, algunos ejemplos de palabras y sus más cercanas según el entrenamiento. Para más detalles, [Ver el notebook del desafío 2](Desafio2/Desafio2_MauroAguirregaray.ipynb):

* **Wind:** No parece tener mucha similitud con el resto de palabras, ya que parece haberse construido considerando a "wind" como proyectos de energía eólica (located, rated, particular, annual, projects) y sus beneficios (economic, higher, technology).

* **Energy:** Aquí se observan dos contextos que se encuentran para la palabra "energy": uno relacionado a la tecnología del futuro y renovable (mechanism, renewable, future, effective, generation), y otro a temas de permisos y promociones estatales (european, permission, union, support).

* **Turbines:** Para "turbines", se encuentra similitud con parques eólicos y varias turbinas juntas.

* **Blade:** En el caso de "blade", se relaciona más bien con conceptos de la física de un perfil aerodinámico, incluyendo elementos que describen al objeto (loss, tip, r, radius) y aquellos que describen al viento con el que interactúa (stationary, element-momentum).

* **Theory:** Este, sin dudas, es el más decepcionante. Se entrena incorrectamente con una mayoría de números, sugiriendo que estos deben hacer referencia a una ecuación. El modelo otorga más importancia a los números de la que debería tener. Un número en particular resulta interesante: el 59, que tiene más similitud. El 0.59 es el conocido como límite de Betz, que hace referencia a la cantidad de energía disponible del viento para generación y es un límite teórico. Es intrigante pensar si esta relación se debe a esa razón o si es mera casualidad.

## Desafío 3

En el desafío anterior se abordaron los embeddings, y con mayores recursos y modelos más complejos es posible comprender de manera superficial cómo se utilizan y generan los principales modelos de embeddings, tales como GloveEmbeddings y FastTextEmbeddings, que fueron utilizados en este curso.

A partir de estos conocimientos, en el [Desafío 3](Desafio3/Desafio_3_modelo_lenguaje_word.ipynb) se plantea un paso siguiente: comenzar a interpretar el contexto de las palabras, permitiendo que los modelos procesen secuencias de texto (oraciones) para predecir las palabras siguientes más probables. Para este desafío, mantuve el mismo tema del Desafío 2, con el objetivo de comprobar si modelos más avanzados, como LSTM y Bidirectional, podían captar un contexto científico más complejo.

En este ejercicio, se exploraron arquitecturas más sofisticadas y la métrica de evaluación utilizada fue la *perplejidad*, que presenta cierta complejidad en su cálculo y fue uno de los principales desafíos debido a la **alta demanda computacional**.

Por las limitaciones de hardware, fue necesario reducir las dimensiones del modelo, implementando arquitecturas más pequeñas. A pesar de las restricciones, los resultados obtenidos fueron muy buenos. [Aquí](Desafio3) se presentan varios ejemplos de predicción de la siguiente palabra.

## Desafío 4

Después de haber trabajado en la vectorización de texto en el Desafío 1, la generación de embeddings en el Desafío 2 y el tratamiento de secuencias con modelos recurrentes más avanzados en el Desafío 3, el siguiente paso fue abordar problemas más complejos y de relevancia cotidiana.

En clase se profundizó en el funcionamiento de los sistemas de traducción automática, y en el [Desafío 4](Desafio4/Desafio_4_bot_qa.ipynb) se propuso la construcción de un bot de preguntas y respuestas, utilizando los conocimientos adquiridos en clase. En este caso, implementé un modelo encoder-decoder para interpretar las preguntas y generar respuestas.

Los resultados obtenidos no fueron los esperados, ya que no logré entrenar un bot que pudiera ofrecer respuestas coherentes. Esto se debió a dificultades tanto en la programación como en la gestión de embeddings, y a la imposibilidad de ajustar los hiperparámetros recomendados en clase para optimizar el entrenamiento del bot.

## Desafío 5

En el último desafío de la materia, se abordó un problema común en la industria: predecir reseñas a partir de comentarios textuales. A su vez, uno de los objetivos principales fue la utilización del modelo BERT, ampliamente reconocido y utilizado en la industria.

El desarrollo de este desafío fue similar a lo visto en clase, aunque se presentaron dificultades técnicas relacionadas con la programación y las dependencias del modelo BERT y TensorFlow. Debido a estos inconvenientes, el estudio fue menos exhaustivo y no se realizaron tantas comparaciones de desempeño al variar los hiperparámetros.

En cuanto a los resultados, el modelo logró identificar adecuadamente reseñas positivas o negativas, incluso en los casos más complejos. Sin embargo, cuando se trataba de reseñas neutras y más elaboradas, la predicción tendía a clasificarlas erroneamente.

## Conclusiones Generales

Este proceso de redacción del README me permitió reflexionar sobre la progresión clara en la dificultad y complejidad de los desafíos abordados a lo largo de la materia, así como las herramientas que fui aprendiendo e implementando.

Si bien se exploraron temas de gran relevancia y aplicación en el ámbito profesional, tengo la sensación de que algunos puntos no fueron completamente asimilados. Esto podría deberse, en parte, al uso de TensorFlow, que requiere menos líneas de código para entrenar en comparación con PyTorch, y a que no se profundizó lo suficiente en clase sobre el funcionamiento detallado de los notebooks. Tal vez habría sido útil haber cursado una materia anterior con modelos más simples, que facilitara una comprensión más sólida de estas herramientas.
