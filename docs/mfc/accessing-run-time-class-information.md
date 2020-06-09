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
ms.openlocfilehash: a9f90640007f84c854d59cc27e0c38459c76fe46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619197"
---
# <a name="accessing-run-time-class-information"></a>Acceso a la información de clases en tiempo de ejecución

En este artículo se explica cómo obtener acceso a información sobre la clase de un objeto en tiempo de ejecución.

> [!NOTE]
> MFC no utiliza la compatibilidad con la [información de tipo en tiempo de ejecución](../cpp/run-time-type-information.md) (RTTI) introducida en Visual C++ 4,0.

Si ha derivado la clase de [CObject](reference/cobject-class.md) y ha utilizado **declare**_**Dynamic** y `IMPLEMENT_DYNAMIC` , `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE` , o las `DECLARE_SERIAL` `IMPLEMENT_SERIAL` macros y explicadas en el artículo [derivar una clase de CObject](deriving-a-class-from-cobject.md), la `CObject` clase tiene la capacidad de determinar la clase exacta de un objeto en tiempo de ejecución.

Esta capacidad resulta muy útil cuando se necesita una comprobación de tipos adicional de argumentos de función y se debe escribir código de propósito especial basado en la clase de un objeto. Sin embargo, esta práctica no suele ser recomendable porque duplica la funcionalidad de las funciones virtuales.

La `CObject` función miembro `IsKindOf` se puede usar para determinar si un objeto determinado pertenece a una clase especificada o si se deriva de una clase específica. El argumento para `IsKindOf` es un `CRuntimeClass` objeto, que se puede obtener mediante la `RUNTIME_CLASS` macro con el nombre de la clase.

### <a name="to-use-the-runtime_class-macro"></a>Para usar la macro RUNTIME_CLASS

1. Use `RUNTIME_CLASS` con el nombre de la clase, como se muestra aquí para la clase `CObject` :

   [!code-cpp[NVC_MFCCObjectSample#4](codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

Rara vez necesitará tener acceso directamente al objeto de clase en tiempo de ejecución. Un uso más común es pasar el objeto de clase en tiempo de ejecución a la `IsKindOf` función, tal como se muestra en el procedimiento siguiente. La `IsKindOf` función prueba un objeto para ver si pertenece a una clase determinada.

#### <a name="to-use-the-iskindof-function"></a>Para usar la función IsKindOf

1. Asegúrese de que la clase tiene compatibilidad de clase en tiempo de ejecución. Es decir, la clase se debe haber derivado directa o indirectamente de `CObject` y ha utilizado **declare**_**Dynamic** y `IMPLEMENT_DYNAMIC` , `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE` , o `DECLARE_SERIAL` las `IMPLEMENT_SERIAL` macros y explicadas en el artículo [derivar una clase de CObject](deriving-a-class-from-cobject.md).

1. Llame a la `IsKindOf` función miembro para los objetos de esa clase, usando la `RUNTIME_CLASS` macro para generar el `CRuntimeClass` argumento, como se muestra aquí:

   [!code-cpp[NVC_MFCCObjectSample#2](codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  IsKindOf devuelve **true** si el objeto es un miembro de la clase especificada o de una clase derivada de la clase especificada. `IsKindOf`no admite varias clases base virtuales o de herencia, aunque se puede usar la herencia múltiple para las clases derivadas de Microsoft Foundation si es necesario.

Un uso de la información de clase en tiempo de ejecución está en la creación dinámica de objetos. Este proceso se describe en el artículo [creación dinámica de objetos](dynamic-object-creation.md).

Para obtener información más detallada sobre la serialización y la información de clase en tiempo de ejecución, vea los artículos [archivos en MFC](files-in-mfc.md) y [serialización](serialization-in-mfc.md).

## <a name="see-also"></a>Consulte también

[Uso de CObject](using-cobject.md)
