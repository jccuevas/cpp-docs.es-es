---
title: "Clases de colección ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DestructElements function
- collection classes, choosing
- ConstructElements function
- SerializeElements function
- traits classes
- collection classes, about collection classes
- CTraits classes
- collection classes
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24b0fbdc5ab68319704fb59746862384198f232b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atl-collection-classes"></a>Clases de colección de ATL
ATL proporciona varias clases para almacenar y obtener acceso a datos. La clase que decida usar depende de varios factores, incluyendo:  
  
-   La cantidad de datos que se almacenan  
  
-   Eficacia frente al rendimiento al obtener acceso a los datos  
  
-   La capacidad para tener acceso a los datos por índice o por clave  
  
-   ¿Cómo se ordenan los datos  
  
-   Preferencias personales  
  
## <a name="small-collection-classes"></a>Clases de colección pequeñas  
 ATL proporciona las siguientes clases de matriz para tratar con un número pequeño de objetos. Sin embargo, estas clases son limitadas y diseñadas para su uso internamente por ATL. No se recomienda usarlos en sus programas.  
  
|Clase|Tipo de almacenamiento de datos|  
|-----------|--------------------------|  
|[CSimpleArray](../atl/reference/csimplearray-class.md)|Implementa una clase de matriz para tratar con un número pequeño de objetos.|  
|[CSimpleMap](../atl/reference/csimplemap-class.md)|Implementa una clase de asignación para tratar con un número pequeño de objetos.|  
  
## <a name="general-purpose-collection-classes"></a>Clases de colección de propósito general  
 Las clases siguientes implementan matrices, listas y mapas y se proporcionan como clases de colección de uso general:  
  
|Clase|Tipo de almacenamiento de datos|  
|-----------|--------------------------|  
|[CAtlArray](../atl/reference/catlarray-class.md)|Implementa una matriz.|  
|[CAtlList](../atl/reference/catllist-class.md)|Implementa una lista.|  
|[CAtlMap](../atl/reference/catlmap-class.md)|Implementa una estructura de asignación, mediante el cual se pueden hacer referencia a datos mediante una clave o valor.|  
|[CRBMap](../atl/reference/crbmap-class.md)|Implementa una estructura de asignación mediante el algoritmo de color rojo y negro.|  
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Implementa una estructura de asignación múltiple rojo-negro rojo y negro.|  
  
 Estas clases interceptan muchos errores de programación cuando se utilizan en las compilaciones de depuración, pero por motivos de rendimiento, estas comprobaciones no se realizará en las compilaciones comerciales.  
  
## <a name="specialized-collection-classes"></a>Clases de colección especializadas  
 También se proporcionan clases de colecciones especializadas para administrar los punteros de memoria y los punteros de interfaz:  
  
|Clase|Propósito|  
|-----------|-------------|  
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|Proporciona métodos útiles para construir una matriz de punteros inteligentes.|  
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|Proporciona métodos útiles al construir una lista de punteros inteligentes.|  
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|Almacenes de `IUnknown` punteros y está diseñado para utilizarse como un parámetro a la [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) clase de plantilla.|  
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|Proporciona métodos útiles al construir una lista de punteros del montón.|  
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|Proporciona métodos útiles para construir una matriz de punteros de interfaz COM.|  
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|Proporciona métodos útiles al construir una lista de punteros de interfaz COM.|  
  
## <a name="choosing-a-collection-class"></a>Elegir una clase de colección  
 Cada una de las clases de colección disponible ofrece distintas características de rendimiento, como se muestra en la tabla siguiente.  
  
-   Las columnas 2 y 3 describen cada clase de ordenación y las características de acceso. En la tabla, el término "ordenado" significa que el orden en el que se insertan o eliminan los elementos determina su orden en la colección; no significa que los elementos se ordenan por su contenido. El término “indexado” significa que los elementos de la colección se pueden recuperar mediante un índice entero, como los elementos de una matriz estándar.  
  
-   Las columnas 4 y 5 describen el rendimiento de cada clase. En aplicaciones que requieren muchas inserciones en la colección, la velocidad de inserción puede ser especialmente importante; para otras aplicaciones, puede ser más importante la velocidad de búsqueda.  
  
-   En la columna 6 se describe si cada forma permite elementos duplicados.  
  
-   El rendimiento de una operación de la clase de colección dada se expresa en términos de la relación entre el tiempo necesario para completar la operación y el número de elementos de la colección. Una operación que tarda una cantidad de tiempo que aumenta linealmente según el número de elementos aumenta se describe como un algoritmo o (n). Por el contrario, una operación que tarda un período de tiempo que aumenta a menos que el número de elementos aumenta se describe como un algoritmo O (n de registro). Por lo tanto, en términos de rendimiento, los algoritmos O (n registro) superan algoritmos o (n) cada vez más como el número de elementos aumenta.  
  
### <a name="collection-shape-features"></a>Características de la forma de colección  
  
|Forma|Por orden |Indizar|Insertar un<br /><br /> elemento|Buscar<br /><br /> elemento especificado|Duplicar<br /><br /> elementos|  
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|  
|Lista|Sí|No|Fast (tiempo constante)|Lento o (n)|Sí|  
|Matriz|Sí|Por int (tiempo constante)|Lento o (n) excepto si se inserta al final, en cuyo momento constante case|Lento o (n)|Sí|  
|Asignación|No|Por clave (tiempo constante)|Fast (tiempo constante)|Fast (tiempo constante)|No (claves) Sí (valores)|  
|Mapa de color rojo y negro|Sí (por clave)|Por clave O (n de registro)|Rápido O (n de registro)|Rápido O (n de registro)|No|  
|Asignación múltiple de color rojo y negro|Sí (por clave)|Clave O(log n) (múltiples valores por clave)|Rápido O (n de registro)|Rápido O (n de registro)|Sí (múltiples valores por clave)|  
  
## <a name="using-ctraits-objects"></a>Uso de objetos CTraits  
 Como las clases de colección de ATL se pueden usar para almacenar una amplia variedad de tipos de datos definidos por el usuario, puede ser útil poder reemplazar funciones importantes como las comparaciones. Esto se logra mediante las clases CTraits.  
  
 Clases CTraits son similares a, pero son más flexibles que las funciones auxiliares de clase de colección de MFC; vea [aplicaciones auxiliares de clase de colección](../mfc/reference/collection-class-helpers.md) para obtener más información.  
  
 Al construir la clase de colección, tiene la opción de especificar una clase CTraits. Esta clase contendrá el código que realizará operaciones tales como comparaciones cuando llama a los otros métodos que componen la clase de colección. Por ejemplo, si el objeto de lista contiene sus propias estructuras definidas por el usuario, puede que desee volver a definir la prueba de igualdad para comparar sólo determinadas variables de miembro. De esta manera, el método Find del objeto de lista funcionará de manera más útil.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="code"></a>Código  
 [!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]  
  
## <a name="comments"></a>Comentarios  
 Para obtener una lista de las clases CTraits, vea [clases de colección](../atl/collection-classes.md).  
  
 El diagrama siguiente muestra la jerarquía de clases para las clases CTraits.  
  
 ![Jerarquía de rasgos de clases de colección](../atl/media/vctraitscollectionclasseshierarchy.gif "vctraitscollectionclasseshierarchy")  
  
## <a name="collection-classes-samples"></a>Ejemplos de clases de colección  
 Los ejemplos siguientes muestran las clases de colección:  
  
-   [Ejemplo MMXSwarm](../visual-cpp-samples.md)  
  
-   [Ejemplo DynamicConsumer](../visual-cpp-samples.md)  
  
-   [Ejemplo UpdatePV](../visual-cpp-samples.md)  
  
-   [Ejemplo de marquesina](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [Clases de colección](../atl/collection-classes.md)

