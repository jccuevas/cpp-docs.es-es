---
title: Clases de colección de ATL
ms.date: 11/19/2018
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
ms.openlocfilehash: 70ca283468a51b4214273698a532ce2a85d52b44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223443"
---
# <a name="atl-collection-classes"></a>Clases de colección de ATL

ATL proporciona muchas clases para almacenar y obtener acceso a datos. La clase que decida usar depende de varios factores, como:

- La cantidad de datos se almacenen

- Eficacia frente al rendimiento al obtener acceso a los datos

- La capacidad de acceder a los datos por índice o por clave

- ¿Cómo se ordenan los datos

- Preferencias personales

## <a name="small-collection-classes"></a>Clases de colección pequeñas

ATL proporciona las siguientes clases de matriz para tratar con un número pequeño de objetos. Sin embargo, estas clases son limitadas y diseñadas para usarse internamente en ATL. No se recomienda usarlas en sus programas.

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
|[CAtlMap](../atl/reference/catlmap-class.md)|Implementa una estructura de asignación, mediante el cual se pueden hacer referencia a datos mediante la clave o valor.|
|[CRBMap](../atl/reference/crbmap-class.md)|Implementa una estructura de asignación mediante el algoritmo rojo-negro.|
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Implementa una estructura de asignación múltiple rojo-negro rojo-negro.|

Estas clases le permite detectar muchos errores de programación cuando se usa en las compilaciones de depuración, pero por motivos de rendimiento, estas comprobaciones no se realizan en las compilaciones comerciales.

## <a name="specialized-collection-classes"></a>Clases de colección especializadas

También se proporcionan clases de colecciones especializadas para administrar los punteros de memoria y los punteros de interfaz:

|Clase|Finalidad|
|-----------|-------------|
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|Proporciona métodos útiles al construir una matriz de punteros inteligentes.|
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|Proporciona métodos útiles al construir una lista de punteros inteligentes.|
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|Almacenes `IUnknown` punteros y está diseñado para usarse como un parámetro a la [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) clase de plantilla.|
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|Proporciona métodos útiles al construir una lista de punteros del montón.|
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|Proporciona métodos útiles al construir una matriz de punteros de interfaz COM.|
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|Proporciona métodos útiles al construir una lista de punteros de interfaz COM.|

## <a name="choosing-a-collection-class"></a>Elección de una clase de colección

Cada una de las clases de colección disponibles ofrece distintas características de rendimiento, tal como se muestra en la tabla siguiente.

- Las columnas 2 y 3 describen cada clase de ordenación y las características de acceso. En la tabla, el término "ordenado" significa que el orden en el que se insertan o eliminan los elementos determina su orden en la colección; no significa que los elementos se ordenan por su contenido. El término “indexado” significa que los elementos de la colección se pueden recuperar mediante un índice entero, como los elementos de una matriz estándar.

- Las columnas 4 y 5 describen el rendimiento de cada clase. En aplicaciones que requieren muchas inserciones en la colección, la velocidad de inserción puede ser especialmente importante; para otras aplicaciones, puede ser más importante la velocidad de búsqueda.

- En la columna 6 se describe si cada forma permite elementos duplicados.

- El rendimiento de una operación de la clase de colección dada se expresa en términos de la relación entre el tiempo necesario para completar la operación y el número de elementos de la colección. Una operación que tarda una cantidad de tiempo que aumenta linealmente a medida que el número de elementos se describe como un algoritmo o (n). Por el contrario, se describe una operación que tarda un período de tiempo que aumenta a menos que el número de elementos aumenta como un algoritmo O (log n). Por lo tanto, en términos de rendimiento, los algoritmos de O (log n) tienen un mayor rendimiento cada vez más, como el número de elementos aumenta.

### <a name="collection-shape-features"></a>Características de la forma de colección

|Forma|Por orden |Indizar|Insertar un<br /><br /> elemento|Buscar<br /><br /> elemento especificado|Duplicar<br /><br /> elementos|
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|
|Lista|Sí|No|Rápido (tiempo constante)|Lento o (n)|Sí|
|Matriz|Sí|Por int (tiempo constante)|Lento o (n), excepto si se inserta al final, en cuyo momento constante case|Lento o (n)|Sí|
|Asignación|No|Por clave (tiempo constante)|Rápido (tiempo constante)|Rápido (tiempo constante)|No (claves) Sí (valores)|
|Mapa rojo-negro|Sí (mediante la clave)|Por clave O (log n)|Rápido O (log n)|Rápido O (log n)|No|
|Rojo-negro|Sí (mediante la clave)|Por clave O(log n) (varios valores por clave)|Rápido O (log n)|Rápido O (log n)|Sí (varios valores por clave)|

## <a name="using-ctraits-objects"></a>Uso de objetos CTraits

Como las clases de colección de ATL se pueden usar para almacenar una amplia gama de tipos de datos definido por el usuario, puede ser útil poder invalidar funciones importantes como las comparaciones. Esto se logra mediante las clases CTraits.

Clases CTraits son similares a, pero más flexibles que las funciones auxiliares de clase de colección de MFC; consulte [aplicaciones auxiliares de clase de colección](../mfc/reference/collection-class-helpers.md) para obtener más información.

Al construir la clase de colección, tiene la opción de especificar una clase CTraits. Esta clase contendrá el código que llevará a cabo operaciones tales como comparaciones cuando llama a los otros métodos que constituyen la clase de colección. Por ejemplo, si el objeto de lista contiene sus propias estructuras definidas por el usuario, es posible que desea volver a la prueba de igualdad para comparar solo ciertas variables de miembro. De este modo, el método Find del objeto de lista funcionará resulta más útil.

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

[!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]

## <a name="comments"></a>Comentarios

Para obtener una lista de las clases CTraits, vea [clases de colección](../atl/collection-classes.md).

El diagrama siguiente muestra la jerarquía de clases para las clases CTraits.

![Jerarquía de rasgos para las clases de colección](../atl/media/vctraitscollectionclasseshierarchy.gif "jerarquía de rasgos para las clases de colección")

## <a name="collection-classes-samples"></a>Ejemplos de clases de colección

Los ejemplos siguientes muestran las clases de colección:

- [Ejemplo MMXSwarm](../overview/visual-cpp-samples.md)

- [DynamicConsumer Sample](../overview/visual-cpp-samples.md)

- [Ejemplo UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

- [Ejemplo de marquesina](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Vea también

[Conceptos](../atl/active-template-library-atl-concepts.md)<br/>
[Clases de colección](../atl/collection-classes.md)
