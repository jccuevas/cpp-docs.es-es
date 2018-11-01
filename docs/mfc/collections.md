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
ms.openlocfilehash: f7ded70431b80257433058cc9af89bcb137c4247
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490862"
---
# <a name="collections"></a>Colecciones

La biblioteca Microsoft Foundation Class proporciona clases de colección para administrar grupos de objetos. Estas clases son de dos tipos:

- [Clases de colección creadas a partir de plantillas de C++](#_core_the_template_based_collection_classes)

- [Clases de colección no creadas a partir de plantillas](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
>  Si el código ya utiliza las clases de colección sin plantilla, puede continuar usarlas. Si escribe nuevas clases de colección con seguridad de tipos para sus propios tipos de datos, se recomienda usar las nuevas clases basadas en plantillas.

##  <a name="_core_collection_shapes"></a> Formas de colección

Una clase de colección se caracteriza por su "forma" y los tipos de sus elementos. La forma hace referencia a la forma en que los objetos se organizan y almacenan en la colección. MFC proporciona tres formas de colección básicas: listas, matrices y mapas (también conocido como diccionarios). Puede elegir la forma de colección que es más adecuada para su problema concreto de programación.

Cada una de las tres formas de colección proporcionada se describe brevemente más adelante en este tema. Para comparar las características de las formas que le ayudarán a decidir cuál es mejor para su programa, vea [recomendaciones para elegir una clase de colección](../mfc/recommendations-for-choosing-a-collection-class.md).

- Lista

   La clase list ofrece una lista ordenada y no indizada de elementos, que se implementa como una lista vinculada por partida doble. Una lista tiene un "encabezado" y "cola" y agregar o quitar elementos de la cabeza final, o insertar o eliminar elementos en el medio, es muy rápida.

- Matriz

   La clase de matriz proporciona una matriz dinámicamente con tamaño, ordenada y entero indexado de objetos.

- Mapa (también conocido como un diccionario)

   Un mapa es una colección que asocia un objeto de clave a un objeto de valor.

##  <a name="_core_the_template_based_collection_classes"></a> Las clases de colección basadas en plantillas

La manera más fácil de implementar una colección con seguridad de tipos que contiene objetos de cualquier tipo es usar una de las clases basadas en plantillas MFC. Para obtener ejemplos de estas clases, vea el ejemplo MFC [recopilar](../visual-cpp-samples.md).

En la tabla siguiente se enumera las clases de colección basadas en plantillas MFC.

### <a name="collection-template-classes"></a>Clases de colección de plantilla

|Contenido de la colección|Matrices|Listas|Asignaciones|
|-------------------------|------------|-----------|----------|
|Colecciones de objetos de cualquier tipo|`CArray`|`CList`|`CMap`|
|Colecciones de punteros a objetos de cualquier tipo|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

##  <a name="_core_the_collection_classes_not_based_on_templates"></a> Las clases de colección no basadas en plantillas

Si la aplicación ya usa las clases MFC sin plantilla, puede continuar usarlas. Sin embargo, para las nuevas colecciones, se recomienda que utilice las clases basadas en plantillas. En la tabla siguiente se enumera las clases de colección de MFC que no se basan en plantillas.

### <a name="nontemplate-collection-classes"></a>Clases de colección no es de plantilla

|Matrices|Listas|Asignaciones|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

Las clases de colección de características de MFC tabla [recomendaciones para elegir una clase de colección](../mfc/recommendations-for-choosing-a-collection-class.md) describe las clases de colección de MFC en cuanto a estas características (que no sea de forma):

- Si la clase usa plantillas de C++

- Si los elementos almacenados en la colección pueden serializarse

- Si los elementos almacenados en la colección pueden volcarse para diagnósticos

- Si la colección tiene seguridad de tipos

### <a name="what-do-you-want-to-do"></a>Qué quieres hacer

#### <a name="general-collection-class-tasks"></a>Tareas generales de clase de colección

- [Recomendaciones para elegir una clase de colección](../mfc/recommendations-for-choosing-a-collection-class.md)

- [Procedimiento para crear una colección con seguridad de tipos](../mfc/how-to-make-a-type-safe-collection.md)

- [Creación de colecciones de pila y de cola](../mfc/creating-stack-and-queue-collections.md)

- [CArray::Add](../mfc/reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>Tareas de la clase de colección basadas en plantillas

- [Clases basadas en plantillas](../mfc/template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Acceso a los miembros de una colección (basadas en plantillas o no)

- [Acceso a todos los miembros de una colección](../mfc/accessing-all-members-of-a-collection.md)

- [Eliminación de todos los objetos de una colección CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)<br/>
[Temas generales de MFC](../mfc/general-mfc-topics.md)

