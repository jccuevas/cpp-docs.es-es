---
title: "Clases de colecci&#243;n de ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de colección"
  - "clases de colección, acerca de las clases de colección"
  - "clases de colección, elegir"
  - "ConstructElements (función)"
  - "clases CTraits"
  - "DestructElements (función)"
  - "SerializeElements (función)"
  - "clases traits"
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Clases de colecci&#243;n de ATL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL proporciona muchas clases para los datos que almacena y de acceso.  Qué clase decide utilizar depende de varios factores, incluyendo:  
  
-   La cantidad de datos que se almacenarán  
  
-   Eficacia de rendimiento en el acceso de los datos  
  
-   La capacidad de tener acceso a los datos por índice o por clave  
  
-   Cómo se ordena los datos  
  
-   Preferencia personal  
  
## Pequeñas clases de colección  
 ATL proporciona las siguientes clases de matriz para tratar con una pequeña cantidad de objetos.  Sin embargo, estas clases están limitadas y que se van a usar internamente para ATL.  No se recomienda que se utilizan en los programas.  
  
|Clase|Tipo de almacenamiento de datos|  
|-----------|-------------------------------------|  
|[CSimpleArray](../atl/reference/csimplearray-class.md)|Implementa una clase array para tratar con una pequeña cantidad de objetos.|  
|[CSimpleMap](../atl/reference/csimplemap-class.md)|Implementa una clase de asignación para tratar con una pequeña cantidad de objetos.|  
  
## Clases de colección de uso general  
 Las clases de siguiente implementan las matrices, listas, y los mapas y se proporcionan como clases de colección de uso general:  
  
|Clase|Tipo de almacenamiento de datos|  
|-----------|-------------------------------------|  
|[CAtlArray](../atl/reference/catlarray-class.md)|Implementa una matriz.|  
|[CAtlList](../atl/reference/catllist-class.md)|Implementa una lista.|  
|[CAtlMap](../atl/reference/catlmap-class.md)|Implementa una estructura de asignación, por el que los datos puedan hacer referencia mediante una clave o un valor.|  
|[CRBMap](../atl/reference/crbmap-class.md)|Implementa una estructura de asignación mediante el algoritmo de Rojo\- Negro.|  
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Implementa una estructura multimapping de Rojo\- Negro.|  
  
 Estas clases interceptarán muchos errores de programación cuando se utilizan en compilaciones de depuración, pero para el motivo de rendimiento, estas comprobaciones no se realizadas en compila comercial.  
  
## Clases de colección especializadas  
 Clases de colección especializadas también se proporcionan para administrar punteros de memoria y punteros de interfaz:  
  
|Clase|Propósito|  
|-----------|---------------|  
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|Proporciona métodos útiles al crear una matriz de punteros inteligentes.|  
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|Proporciona métodos útiles al crear una lista de punteros inteligentes.|  
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|Almacena los punteros de `IUnknown` y es utilizado como parámetro a la clase de plantilla de [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) .|  
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|Proporciona métodos útiles al crear una lista de punteros de la pila.|  
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|Proporciona métodos útiles al crear una matriz de punteros de interfaz COM.|  
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|Proporciona métodos útiles al crear una lista de punteros de interfaz COM.|  
  
## Elegir una clase de colección  
 Cada una de las clases de colección disponibles proporciona varias características de rendimiento, como se muestra en la siguiente tabla.  
  
-   Las columnas 2 y 3 se describe cada tipo de ordenación y tienen acceso a características.  En la tabla, el término “orden” significa que el orden en que se insertan y se eliminan los elementos determina el orden en la colección; no significa que los elementos se ordenan en su contenido.  El término “indizó” significa que los elementos de la colección se pueden recuperar mediante un índice entero, como elementos de una matriz estándar.  
  
-   Las columnas 4 y 5 describen el rendimiento de cada clase.  En aplicaciones que requieren muchas inserciones en la colección, la velocidad de inserción puede ser especialmente importante; en otras aplicaciones, la velocidad de búsqueda puede ser más importante.  
  
-   la columna 6 describe si cada forma permite elementos duplicados.  
  
-   El rendimiento de una operación determinada de la clase de colección se expresa en términos de relación entre el tiempo necesario para completar la operación y el número de elementos de la colección.  Una operación que toma una cantidad de tiempo que aumenta linealmente como el número de mejoras de elementos se describe como O \(n\) algoritmo.  Por el contrario, una operación que toma un período de tiempo que aumenta cada vez menos como el número de mejoras de elementos se describe como O \(algoritmo log n\).  Por consiguiente, en términos de rendimiento, O \(algoritmos de log n\) supera O \(n\) los algoritmos cada vez más como el número de elementos aumenta.  
  
### Características de la colección  
  
|Forma|¿Secuenciado?|¿Indizado?|Inserte<br /><br /> element|Buscar<br /><br /> elemento especificado|Duplicado<br /><br /> ¿elementos?|  
|-----------|-------------------|----------------|-------------------------|--------------------------------------|-------------------------------|  
|List|Sí|No|Rápido \(tiempo constante\)|o lento \(n\)|Sí|  
|Matriz|Sí|Por int \(tiempo constante\)|Reduzca O \(n\) excepto si inserta al final, en este caso es constante sincronizar|o lento \(n\)|Sí|  
|Mapa|No|Por clave \(tiempo constante\)|Rápido \(tiempo constante\)|Rápido \(tiempo constante\)|Ningún Sí \(keys\) \(valores\)|  
|Mapa de Rojo\- Negro|Sí \(por clave\)|Mediante una clave O \(log n\)|Rápido o \(log n\)|Rápido o \(log n\)|No|  
|Rojo\-Negro Multimap|Sí \(por clave\)|Mediante una clave O \(log n\) \(varios valores por clave\)|Rápido o \(log n\)|Rápido o \(log n\)|Sí \(varios valores por clave\)|  
  
## Mediante los objetos de CTraits  
 Mientras que las clases de colección ATL se pueden utilizar para almacenar una amplia gama de tipos de datos definidos por el usuario, puede ser útil poder reemplazar funciones importantes como comparaciones.  Esto se logra utilizando las clases de CTraits.  
  
 Las clases de CTraits son similares a, pero más flexibles que, las funciones auxiliares de la clase de colección MFC; vea [Aplicaciones auxiliares de clase de colección](../mfc/reference/collection-class-helpers.md) para obtener más información.  
  
 Al crear la clase de colección, tiene la opción de especificar una clase de CTraits.  Esta clase contendrá código que realizará operaciones como comparaciones cuando es llamado por los demás métodos que constituyen la clase de colección.  Por ejemplo, si el objeto de la lista contiene sus propias estructuras definidas por el usuario, desea volver a definir la prueba de igualdad para comparar solo a determinadas variables miembro.  De esta manera, el método de búsqueda del objeto de lista funcionará de una manera más útil.  
  
## Ejemplo  
  
### Código  
 [!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/CPP/atl-collection-classes_1.cpp)]  
  
## Comentarios  
 Para obtener una lista de las clases de CTraits, vea [clases de colección](../atl/collection-classes.md).  
  
 El diagrama siguiente muestra la jerarquía de clases para las clases de CTraits.  
  
 ![Jerarquía de rasgos de clases de colección](../atl/media/vctraitscollectionclasseshierarchy.png "vcTraitsCollectionClassesHierarchy")  
  
## Ejemplos de las clases de colección  
 Los ejemplos siguientes muestran las clases de colección:  
  
-   [Ejemplo MMXSwarm](../top/visual-cpp-samples.md)  
  
-   [Ejemplo DynamicConsumer](../top/visual-cpp-samples.md)  
  
-   [Ejemplo UpdatePV](../top/visual-cpp-samples.md)  
  
-   [Ejemplo de la marquesina](../top/visual-cpp-samples.md)  
  
## Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [Clases de colección](../atl/collection-classes.md)