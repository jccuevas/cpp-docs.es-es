---
title: Colecciones
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, collections
- arrays [MFC], classes
- MFC collection classes
- shapes, collection
- collection classes [MFC], MFC
- collections, about collections
- array templates [MFC]
- collection classes [MFC], template-based
- collection classes [MFC], about collection classes
- collection classes [MFC], maps
- collection classes [MFC], arrays
- shapes
- collection classes [MFC], lists
- collection classes [MFC], shapes
ms.assetid: 02586e4c-851d-41d0-a722-feb11c17c74c
ms.openlocfilehash: 3fba3a3c6cd3fecbda7f46575b1d72c450c44019
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361862"
---
# <a name="collections"></a>Colecciones

La biblioteca Microsoft Foundation Class proporciona clases de colección para administrar grupos de objetos. Estas clases son de dos tipos:

- [Clases de colección creadas a partir de plantillas C++](#_core_the_template_based_collection_classes)

- [Clases de colección no creadas a partir de plantillas](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
> Si el código ya usa clases de colección que no son de plantilla, puede seguir utilizándolas. Si escribe nuevas clases de colección con seguridad de tipos para sus propios tipos de datos, le recomendamos que utilice las clases basadas en plantillas más recientes.

## <a name="collection-shapes"></a><a name="_core_collection_shapes"></a>Formas de colección

Una clase de colección se caracteriza por su "forma" y por los tipos de sus elementos. La forma hace referencia a la forma en que la colección organiza y almacena los objetos. MFC proporciona tres formas de colección básicas: listas, matrices y mapas (también conocidos como diccionarios). Puede elegir la forma de colección que mejor se adapte a su problema de programación en particular.

Cada una de las tres formas de colección proporcionadas se describe brevemente más adelante en este tema. Para comparar las características de las formas para ayudarle a decidir cuál es el mejor para su programa, consulte [Recomendaciones para elegir una clase](../mfc/recommendations-for-choosing-a-collection-class.md)de colección .

- List

   La clase list proporciona una lista ordenada y no indizada de elementos, implementada como una lista doblemente vinculada. Una lista tiene una "cabeza" y una "cola", y agregar o quitar elementos de la cabeza o la cola, o insertar o eliminar elementos en el medio, es muy rápido.

- Array

   La clase de matriz proporciona una matriz de objetos de tamaño dinámico, ordenada e indizada de enteros.

- Mapa (también conocido como diccionario)

   Un mapa es una colección que asocia un objeto clave con un objeto de valor.

## <a name="the-template-based-collection-classes"></a><a name="_core_the_template_based_collection_classes"></a>Las clases de colección basadas en plantillas

La forma más sencilla de implementar una colección con seguridad de tipos que contiene objetos de cualquier tipo es usar una de las clases basadas en plantillas MFC. Para obtener ejemplos de estas clases, vea el ejemplo de MFC [COLLECT](../overview/visual-cpp-samples.md).

En la tabla siguiente se enumeran las clases de colección basadas en plantillas MFC.

### <a name="collection-template-classes"></a>Clases de plantilla de colección

|Contenido de la colección|Matrices|Listas|Mapas|
|-------------------------|------------|-----------|----------|
|Colecciones de objetos de cualquier tipo|`CArray`|`CList`|`CMap`|
|Colecciones de punteros a objetos de cualquier tipo|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

## <a name="the-collection-classes-not-based-on-templates"></a><a name="_core_the_collection_classes_not_based_on_templates"></a>Las clases de colección no basadas en plantillas

Si la aplicación ya usa clases MFC que no son de plantilla, puede seguir utilizándolas. Sin embargo, para las nuevas colecciones, se recomienda usar las clases basadas en plantillas. En la tabla siguiente se enumeran las clases de colección MFC que no se basan en plantillas.

### <a name="nontemplate-collection-classes"></a>Clases de colección sin plantillas

|Matrices|Listas|Mapas|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

La tabla Características de clases de colección MFC en [Recomendaciones para elegir una clase](../mfc/recommendations-for-choosing-a-collection-class.md) de colección describe las clases de colección MFC en términos de estas características (distintas de la forma):

- Si la clase usa plantillas de C++

- Si los elementos almacenados en la colección pueden serializarse

- Si los elementos almacenados en la colección pueden volcarse para diagnósticos

- Si la colección tiene seguridad de tipos

### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

#### <a name="general-collection-class-tasks"></a>Tareas generales de clase de colección

- [Recomendaciones para elegir una clase de colección](../mfc/recommendations-for-choosing-a-collection-class.md)

- [Procedimiento para crear una colección con seguridad de tipos](../mfc/how-to-make-a-type-safe-collection.md)

- [Crear colecciones de pila y de cola](../mfc/creating-stack-and-queue-collections.md)

- [CArray::Add](../mfc/reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>Tareas de clase de colección basadas en plantillas

- [Clases basadas en plantillas](../mfc/template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Acceso a los miembros de una colección (basado en plantillas o no)

- [Acceso a todos los miembros de una colección](../mfc/accessing-all-members-of-a-collection.md)

- [Eliminación de todos los objetos de una colección CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>Consulte también

[Conceptos](../mfc/mfc-concepts.md)<br/>
[Temas generales de MFC](../mfc/general-mfc-topics.md)
