---
title: Acceso a la información de clase en tiempo de ejecución | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61da17093d56dcfd8b0eeec3ade7955f27bc6b85
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077723"
---
# <a name="accessing-run-time-class-information"></a>Acceso a la información de clases en tiempo de ejecución

En este artículo se explica cómo obtener acceso a información acerca de la clase de un objeto en tiempo de ejecución.

> [!NOTE]
>  MFC no utiliza la [información de tipo de tiempo de ejecución](../cpp/run-time-type-information.md) compatibilidad (RTTI) introducido en Visual C++ 4.0.

Si ha derivado la clase de [CObject](../mfc/reference/cobject-class.md) y utiliza el **DECLARE**_**dinámica** y `IMPLEMENT_DYNAMIC`, el `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE`, o el `DECLARE_SERIAL` y `IMPLEMENT_SERIAL` macros se explican en el artículo [derivar una clase de CObject](../mfc/deriving-a-class-from-cobject.md), el `CObject` clase tiene la capacidad para determinar la clase exacta de un objeto en tiempo de ejecución.

Esta capacidad es muy útil cuando se necesita la comprobación de argumentos de función de tipo adicional y cuando se debe escribir código especial basado en la clase de un objeto. Sin embargo, esta práctica no se suele recomendar porque duplica la funcionalidad de las funciones virtuales.

El `CObject` función miembro `IsKindOf` puede usarse para determinar si un objeto determinado pertenece a una clase especificada o si se deriva de una clase específica. El argumento `IsKindOf` es un `CRuntimeClass` objeto, que puede obtener utilizando el `RUNTIME_CLASS` macro con el nombre de la clase.

### <a name="to-use-the-runtimeclass-macro"></a>Para usar la macro RUNTIME_CLASS

1. Use `RUNTIME_CLASS` con el nombre de la clase, como se muestra aquí para la clase `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

Prácticamente no necesitarán tener acceso al objeto de clase en tiempo de ejecución directamente. Un uso más común consiste en pasar el objeto de clase de tiempo de ejecución para el `IsKindOf` funcione, como se muestra en el procedimiento siguiente. El `IsKindOf` función comprueba un objeto para ver si pertenece a una clase determinada.

#### <a name="to-use-the-iskindof-function"></a>Para usar la función IsKindOf

1. Asegúrese de que la clase tiene compatibilidad de la clase de tiempo de ejecución. Es decir, la clase debe haber sido derivada directa o indirectamente de `CObject` y utiliza el **DECLARE**_**dinámica** y `IMPLEMENT_DYNAMIC`, el `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE`, o el `DECLARE_SERIAL` y `IMPLEMENT_SERIAL` macros se explican en el artículo [derivar una clase de CObject](../mfc/deriving-a-class-from-cobject.md).

1. Llame a la `IsKindOf` función miembro para objetos de esa clase, utilizando el `RUNTIME_CLASS` macro para generar el `CRuntimeClass` argumento, como se muestra aquí:

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  IsKindOf devuelve **TRUE** si el objeto es un miembro de la clase especificada o de una clase derivada de la clase especificada. `IsKindOf` no admite herencia múltiple o clases base virtuales, aunque puede usar herencia múltiple para las clases derivadas de Microsoft Foundation si es necesario.

Un uso de la información de clases en tiempo de ejecución está en la creación dinámica de objetos. Este proceso se describe en el artículo [creación dinámica de objetos](../mfc/dynamic-object-creation.md).

Para obtener más información sobre la serialización y la información de clases en tiempo de ejecución, consulte los artículos [archivos en MFC](../mfc/files-in-mfc.md) y [serialización](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Vea también

[Uso de CObject](../mfc/using-cobject.md)

