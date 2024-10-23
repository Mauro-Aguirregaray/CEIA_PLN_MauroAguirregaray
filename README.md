<img src="https://github.com/hernancontigiani/ceia_memorias_especializacion/raw/master/Figures/logoFIUBA.jpg" width="500" align="center">

# Procesamiento de Lenguaje Natural

Este repositorio pertenece a Mauro Aguirregaray, alumno de la 15a Cohorte de la Especialización en Inteligencia Artificial. Contiene los cinco desafíos realizados para la materia de Procesamiento de Lenguaje Natural. Los trabajos están presentados en Jupyter Notebooks, junto con imágenes que muestran los resultados de diferentes modelos de procesamiento de lenguaje, incrementando su complejidad progresivamente.

A continuación, se ofrece un resumen de cada desafío y sus respectivos resultados.

## Desafío 1

En esta primera experiencia, se trabajó con modelos básicos de procesamiento de texto. Se exploró la vectorización de documentos y palabras, y se evaluó la capacidad de comparación utilizando la *similaridad del coseno*. 

A pesar de la simplicidad del enfoque, los resultados fueron satisfactorios, particularmente en la predicción de la temática de los documentos, aplicando un preprocesamiento ligero de los datos y un modelo básico de *Naive Bayes*. Sin embargo, al aplicar esta metodología a palabras, los resultados no fueron tan alentadores, demostrando la necesidad de emplear modelos más complejos para capturar mejor las relaciones semánticas, lo cual se abordará en los siguientes desafíos.

## Desafío 2

En este desafío se aborda el tema anterior y se busca entrenar *embeddings* de palabras para comprobar si, de esta manera, logramos encontrar similitudes. Para este caso, se toma un tema de interés personal, que en mi caso es la energía eólica.

Aquí aprendimos a trabajar con archivos de texto genéricos, en particular, un libro científico en formato PDF, realizar el preprocesamiento necesario y entrenar los *embeddings*.

Los resultados obtenidos son, sin duda, mejores que los del Desafío 1, aunque las limitaciones de técnicas y de hardware siguen presentando problemas. A continuación, algunos ejemplos de palabras y sus más cercanas según el entrenamiento. Para más detalles, [Ver el notebook del desafío 2](Desafio2/Desafio2_MauroAguirregaray.ipynb):

* **Wind:** No parece tener mucha similitud con el resto de palabras, ya que parece haberse construido considerando a "wind" como proyectos de energía eólica (located, rated, particular, annual, projects) y sus beneficios (economic, higher, technology).

* **Energy:** Aquí se observan dos contextos que se encuentran para la palabra "energy": uno relacionado a la tecnología del futuro y renovable (mechanism, renewable, future, effective, generation), y otro a temas de permisos y promociones estatales (european, permission, union, support).

* **Turbines:** Para "turbines", se encuentra similitud con parques eólicos y varias turbinas juntas.

* **Blade:** En el caso de "blade", se relaciona más bien con conceptos de la física de un perfil aerodinámico, incluyendo elementos que describen al objeto (loss, tip, r, radius) y aquellos que describen al viento con el que interactúa (stationary, element-momentum).

* **Theory:** Este, sin dudas, es el más decepcionante. Se entrena incorrectamente con una mayoría de números, sugiriendo que estos deben hacer referencia a una ecuación. El modelo otorga más importancia a los números de la que debería tener. Un número en particular resulta interesante: el 59, que tiene más similitud. El 0.59 es el conocido como límite de Betz, que hace referencia a la cantidad de energía disponible del viento para generación y es un límite teórico. Es intrigante pensar si esta relación se debe a esa razón o si es mera casualidad.
