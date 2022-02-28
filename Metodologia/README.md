![Logo de Plenna](/assets/logo.png)

# Metodología de trabajo en Plenna

## **Contenido**

En este documento se definen algunos de los pasos del proceso de desarrollo que seguimos dentro de Plenna.

1. [Diseño de solución](#diseño-de-solución)
2. [Diseño de arquitectura](#diseño-de-arquitectura)
3. [Desarrollo](#desarrollo)
4. [Pruebas unitarias](#pruebas-unitarias)
5. [Code review](#code-review)
6. [Testing and QA](#testing-and-qa)
7. [Despliegue a producción](#despliegue-a-producción)

### **Diseño de solución**

El paso más importante del proceso de desarrollo. Una vez que se nos ha entregado un nuevo feature o requerimiento es planear la solución, diseñando los distintos componentes que conformarán la solución, así como los algoritmos y la lógica con la que se comunicarán.

En este paso se pueden crear diagramas de flujo y pseudo código que nos sirvan como documentación del proyecto y la solución implementada. Este proceso puede ser realizado individualmente, aunque se sugiere fuertemente que se incluya a la mayor cantidad posible de personas para obtener distintos puntos de vista y diseñar una solución más robusta.

### **Diseño de arquitectura**

Completamente de la mano con el punto anterior, si el proyecto que estamos diseñando necesita de distintas plataformas o aplicaciones que tendrán que comunicarse entre ellas, uno de los entregables del diseño de solución es un diagrama de arquitectura. En este se especifican las aplicaciones y cómo es que se comunican. Además de este diagrama, también es útil generar diagramas de secuencia, en los que no sólo se muestre cómo se comunican las plataformas, sino que además se muestre el orden y el algoritmo que se cumple con esta comunicación.

### **Nomenclatura y organización de Github**

Utilizamos la metodología de [Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow). Si bien es posible hacer toda una documentación sobre este tema tan extenso, remarcaremos aquí solamente algunos puntos importantes:

- La rama principal, desplegada en producción es la de `master`. Ningún desarrollador podrá hacer un push directo a esta rama, sino que solamente las ramas de hotfix o release pueden ser integrados a través de un Pull Request.
- Cada desarrollador puede crear ramas independientes para sus desarrollos, cada una de ellas debe tener la nomenclatura `feature/nombreDelFeature` en donde podemos utilizar el prefijo **feature** cuando se esté trabajando en un requerimiento nuevo, **hotfix** cuando se esté resolviendo un bug presente en producción y que es tan grave que debe ser resuelto y desplegado unitariamente y directamente a producción y **release** cuando se necesite contener el código de muchos desarrolladores para cumplir con distintos requerimientos que deben ser desplegados juntos.

Finalmente, el Pull Request es el proceso principal a través del cual podemos integrar el código entre distintas features. Cada uno de ellos debe tener un reviewer asignado que debe comprobar la calidad del código.

### **Desarrollo**

Este paso es el más subjetivo de todos, sin embargo, el resto de las guías dentro de este repositorio nos ayudan a estandarizar y definir las mejores prácticas.

### **Pruebas unitarias**

Estas pruebas previas a la entrega con los stakeholders se realizan sobre la unidad de código a entregarse, ya sea un feature o un conjunto de ellos que cumplan el requerimiento en cuestión, debe realizarlas el desarrollador para asegurarse de que el proceso de calidad sea más eficiente y corto. En el mejor de los escenarios, se debe implementar una matriz de pruebas en la que se documenten los escenarios probados y los resultados de los mismos.

También en el mejor de los escenarios, estas pruebas deben ser automatizadas.

### **Code review**

Una vez que se ha asegurado la calidad del código a entregar debe pasar a una revisión previa a ser integrado en el código fuente. Este proceso debe realizarse a través de un Pull Request con destino a la rama del feature que se está trabajando. El código será evaluado basándose en los estándares definidos en este repositorio, el performance del mismo y el grado en que cumple con la solución requerida.

Si fuera necesario, el revisor puede regresar el Pull Request con los bugs o cambios solicitados para que el desarrollador los resuelva. Este proceso puede acelerarse a través del _peer progamming_ si estos dos desarrolladores lo creen necesario.

Una vez que el código cumpla con todos los requerimientos del revisor, será integrado dentro de la rama base del feature para ser probado por los stakeholders principales previo a su paso a producción. Esta integración debe realizarse utilizando merge, evitando squash o rebase, para mantener la misma historia dentro de las distintas ramas, minimizando la probabilidad de errores.

### **Testing and QA**

Este proceso es realizado principalmente por los stakeholders y consiste en comprobar que el producto entregado por el equipo técnico cumple con las expectativas planteadas y ofrece el valor solicitado al paciente o usuario final.

La aportación del equipo técnico dentro de este proceso es la de resolver los bugs encontrados y asistir en las dudas que puedan surgir a lo largo de las pruebas.

### **Despliegue a producción**

Una vez que tanto el equipo técnico como los stakeholders dan el visto bueno al producto desarrollado, es momento de pasar la rama pertinente a producción a través de un despliegue en la herramienta de Amazon Web Services Amplify. Una vez que la versión está desplegada, es necesario también pasar el código fuente productivo a la rama _master_ para que siempre esté sincronizado.
