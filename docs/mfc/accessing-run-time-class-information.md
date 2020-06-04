---
title: Acceso a la información de clases en tiempo de ejecución
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], and RTTI
- CObject class [MFC], using IsKindOf method [MFC]
- run time [MFC], class information
- RUNTIME_CLASS macro [MFC]
- CObject class [MFC], using RUNTIME_CLASS macro [MFC]
- RTTI compiler option [MFC]
- CObject class [MFC], accessing run-time class information
- run time [MFC]
- IsKindOf method method [MFC]
- run-time class [MFC], accessing information
- classes [MFC], run-time class information
- run-time class [MFC]
- RUNTIME_CLASS macro, using
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
ms.openlocfilehash: 4a836bb7bd03bd6654e5c940442fecf541042fd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354227"
---
# <a name="accessing-run-time-class-information"></a>Acceso a la información de clases en tiempo de ejecución

En este artículo se explica cómo obtener acceso a información sobre la clase de un objeto en tiempo de ejecución.

> [!NOTE]
> MFC no utiliza la compatibilidad con información de tipo de tiempo de [ejecución](../cpp/run-time-type-information.md) (RTTI) introducida en Visual C++ 4.0.

Si ha derivado la clase de [CObject](../mfc/reference/cobject-class.md) y `IMPLEMENT_DYNAMIC`ha `DECLARE_DYNCREATE` utilizado `IMPLEMENT_DYNCREATE`el `DECLARE_SERIAL` **DECLARE**_**DYNAMIC** y , el y , o las `IMPLEMENT_SERIAL` macros explicadas en el artículo [Derivado de una clase de CObject](../mfc/deriving-a-class-from-cobject.md), la `CObject` clase tiene la capacidad de determinar la clase exacta de un objeto en tiempo de ejecución.

Esta capacidad es más útil cuando se necesita una comprobación de tipos adicionales de argumentos de función y cuando se debe escribir código de propósito especial basado en la clase de un objeto. Sin embargo, esta práctica no suele ser recomendada porque duplica la funcionalidad de las funciones virtuales.

La `CObject` función `IsKindOf` miembro se puede utilizar para determinar si un objeto determinado pertenece a una clase especificada o si se deriva de una clase específica. El argumento `IsKindOf` to `CRuntimeClass` es un objeto, `RUNTIME_CLASS` que puede obtener utilizando la macro con el nombre de la clase.

### <a name="to-use-the-runtime_class-macro"></a>Para utilizar la macro RUNTIME_CLASS

1. Utilice `RUNTIME_CLASS` con el nombre de la clase, `CObject`como se muestra aquí para la clase:

   [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

Rara vez necesitará tener acceso al objeto de clase en tiempo de ejecución directamente. Un uso más común es pasar el objeto `IsKindOf` de clase en tiempo de ejecución a la función, como se muestra en el siguiente procedimiento. La `IsKindOf` función prueba un objeto para ver si pertenece a una clase determinada.

#### <a name="to-use-the-iskindof-function"></a>Para utilizar la función IsKindOf

1. Asegúrese de que la clase tiene compatibilidad con clases en tiempo de ejecución. Es decir, la clase debe haberse derivado `CObject` directa o indirectamente de `DECLARE_DYNCREATE` `IMPLEMENT_DYNCREATE`y utilizado `DECLARE_SERIAL` `IMPLEMENT_SERIAL` **el DECLARE**_**DYNAMIC** y `IMPLEMENT_DYNAMIC`, el y , o las macros explicadas en el artículo Derivado de [una clase de CObject](../mfc/deriving-a-class-from-cobject.md).

1. Llame `IsKindOf` a la función miembro para `RUNTIME_CLASS` los objetos de esa clase, utilizando la macro para generar el `CRuntimeClass` argumento, como se muestra aquí:

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  IsKindOf devuelve **TRUE** si el objeto es un miembro de la clase especificada o de una clase derivada de la clase especificada. `IsKindOf`no admite varias clases base virtuales o de herencia, aunque puede usar varias herencias para las clases derivadas de Microsoft Foundation si es necesario.

Un uso de la información de clase en tiempo de ejecución se encuentra en la creación dinámica de objetos. Este proceso se describe en el artículo Creación dinámica de [objetos](../mfc/dynamic-object-creation.md).

Para obtener información más detallada sobre la serialización y la información de clase en tiempo de ejecución, vea los artículos [Archivos en MFC](../mfc/files-in-mfc.md) y [serialización](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Consulte también

[Uso de CObject](../mfc/using-cobject.md)
