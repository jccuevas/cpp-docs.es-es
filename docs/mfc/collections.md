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
ms.openlocfilehash: f2cd03afbb09dff38298454658c3d3dc2dfa6a8a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619350"
---
# <a name="collections"></a>Colecciones

El biblioteca MFC proporciona clases de colección para administrar grupos de objetos. Estas clases son de dos tipos:

- [Clases de colección creadas a partir de plantillas de C++](#_core_the_template_based_collection_classes)

- [Clases de colección no creadas a partir de plantillas](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
> Si el código ya usa clases de colección que no son de plantilla, puede seguir utilizándolos. Si escribe nuevas clases de colección con seguridad de tipos para sus propios tipos de datos, se recomienda usar las clases basadas en plantillas más recientes.

## <a name="collection-shapes"></a><a name="_core_collection_shapes"></a>Formas de colección

Una clase de colección se caracteriza por su "forma" y por los tipos de sus elementos. La forma hace referencia a la forma en que los objetos se organizan y almacenan en la colección. MFC proporciona tres formas de colección básicas: listas, matrices y asignaciones (también conocidas como diccionarios). Puede elegir la forma de la colección que sea más adecuada para su problema de programación concreto.

Cada una de las tres formas de colección proporcionadas se describe brevemente más adelante en este tema. Para comparar las características de las formas con el fin de ayudarle a decidir cuál es la mejor opción para su programa, vea [recomendaciones para elegir una clase de colección](recommendations-for-choosing-a-collection-class.md).

- Lista

   La clase List proporciona una lista ordenada y no indizada de elementos, implementada como una lista de doble vínculo. Una lista tiene un "encabezado" y un "final", y agregar o quitar elementos del encabezado o del final, o insertar o eliminar elementos en el centro, es muy rápido.

- Array

   La clase Array proporciona una matriz de objetos de tamaño dinámico, ordenada y con índice entero.

- Map (también conocido como diccionario)

   Una asignación es una colección que asocia un objeto de clave a un objeto de valor.

## <a name="the-template-based-collection-classes"></a><a name="_core_the_template_based_collection_classes"></a>Clases de colección basadas en plantillas

La manera más fácil de implementar una colección con seguridad de tipos que contiene objetos de cualquier tipo es usar una de las clases basadas en plantillas de MFC. Para obtener ejemplos de estas clases, vea el ejemplo de MFC [Collect](../overview/visual-cpp-samples.md).

En la tabla siguiente se enumeran las clases de colección basadas en plantillas de MFC.

### <a name="collection-template-classes"></a>Clases de plantilla de colección

|Contenido de la colección|Matrices|Listas|Maps|
|-------------------------|------------|-----------|----------|
|Colecciones de objetos de cualquier tipo|`CArray`|`CList`|`CMap`|
|Colecciones de punteros a objetos de cualquier tipo|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

## <a name="the-collection-classes-not-based-on-templates"></a><a name="_core_the_collection_classes_not_based_on_templates"></a>Clases de colección no basadas en plantillas

Si su aplicación ya usa clases que no son de plantilla de MFC, puede seguir utilizándolos. Sin embargo, para las nuevas colecciones, se recomienda usar las clases basadas en plantillas. En la tabla siguiente se enumeran las clases de colección de MFC que no están basadas en plantillas.

### <a name="nontemplate-collection-classes"></a>Clases de colección que no son de plantilla

|Matrices|Listas|Maps|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

Características de las clases de colección de MFC en [recomendaciones para elegir una clase de colección](recommendations-for-choosing-a-collection-class.md) se describen las clases de colección de MFC en términos de estas características (distintas de la forma):

- Si la clase usa plantillas de C++

- Si los elementos almacenados en la colección pueden serializarse

- Si los elementos almacenados en la colección pueden volcarse para diagnósticos

- Si la colección tiene seguridad de tipos

### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

#### <a name="general-collection-class-tasks"></a>Tareas generales de clase de colección

- [Recomendaciones para elegir una clase de colección](recommendations-for-choosing-a-collection-class.md)

- [Procedimiento para crear una colección con seguridad de tipos](how-to-make-a-type-safe-collection.md)

- [Crear colecciones de pila y de cola](creating-stack-and-queue-collections.md)

- [CArray:: Add](reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>Tareas de clase de colección basadas en plantillas

- [Clases basadas en plantillas](template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Obtener acceso a los miembros de una colección (basada en plantillas o no)

- [Obtener acceso a todos los miembros de una colección](accessing-all-members-of-a-collection.md)

- [Eliminación de todos los objetos de una colección CObject](deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>Consulte también

[Conceptos](mfc-concepts.md)<br/>
[Temas generales de MFC](general-mfc-topics.md)
