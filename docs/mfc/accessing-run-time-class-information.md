---
title: "Acceso a la información de clase en tiempo de ejecución | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5cdc520118c0d50590927a88de816a593ea5e146
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="accessing-run-time-class-information"></a>Acceso a la información de clases en tiempo de ejecución
Este artículo explica cómo obtener acceso a información sobre la clase de un objeto en tiempo de ejecución.  
  
> [!NOTE]
>  MFC no utiliza la [información de tipo de tiempo de ejecución](../cpp/run-time-type-information.md) compatibilidad de (RTTI) introducida en Visual C++ 4.0.  
  
 Si ha derivado una clase de [CObject](../mfc/reference/cobject-class.md) y utiliza el **DECLARE**_**dinámica** y `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE`, o la `DECLARE_SERIAL` y `IMPLEMENT_SERIAL` macros que se explican en el artículo [derivar una clase de CObject](../mfc/deriving-a-class-from-cobject.md), la `CObject` clase tiene la capacidad para determinar la clase exacta de un objeto en tiempo de ejecución.  
  
 Esta capacidad es muy útil cuando se necesita la comprobación de argumentos de función de tipo adicional y cuándo se debe escribir código especial basado en la clase de un objeto. Sin embargo, esta práctica no se recomienda normalmente porque duplica la funcionalidad de funciones virtuales.  
  
 El `CObject` función miembro `IsKindOf` puede utilizarse para determinar si un objeto determinado pertenece a una clase especificada o si se deriva de una clase específica. El argumento `IsKindOf` es un `CRuntimeClass` objeto, que puede obtener utilizando la `RUNTIME_CLASS` macro con el nombre de la clase.  
  
### <a name="to-use-the-runtimeclass-macro"></a>Para usar la macro RUNTIME_CLASS  
  
1.  Use `RUNTIME_CLASS` con el nombre de la clase, como se muestra aquí para la clase `CObject`:  
  
     [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]  
  
 Rara vez necesitará tener acceso directamente al objeto de clase en tiempo de ejecución. Un uso más común consiste en pasar el objeto de clase en tiempo de ejecución a la `IsKindOf` funcione, tal como se muestra en el procedimiento siguiente. El `IsKindOf` función comprueba un objeto para ver si pertenece a una clase determinada.  
  
#### <a name="to-use-the-iskindof-function"></a>Usar la función IsKindOf  
  
1.  Asegúrese de que la clase tiene compatibilidad con clases de tiempo de ejecución. Es decir, la clase debe se han derivado directa o indirectamente de `CObject` y utiliza el **DECLARE**_**dinámica** y `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE`, o la `DECLARE_SERIAL` y `IMPLEMENT_SERIAL` macros que se explican en el artículo [derivar una clase de CObject](../mfc/deriving-a-class-from-cobject.md).  
  
2.  Llame a la `IsKindOf` función miembro para objetos de esa clase, usando la `RUNTIME_CLASS` macro para generar el `CRuntimeClass` argumento, como se muestra aquí:  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]  
  
     [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]  
  
    > [!NOTE]
    >  IsKindOf devuelve **TRUE** si el objeto es un miembro de la clase especificada o de una clase derivada de la clase especificada. `IsKindOf`no se admite la herencia múltiple o las clases base virtuales, aunque puede usar herencia múltiple para las clases de Microsoft Foundation derivadas si es necesario.  
  
 Uno de los usos de la información de clase en tiempo de ejecución es la creación dinámica de objetos. Este proceso se describe en el artículo [creación dinámica de objetos](../mfc/dynamic-object-creation.md).  
  
 Para obtener más información sobre la serialización y la información de clase en tiempo de ejecución, consulte los artículos [archivos en MFC](../mfc/files-in-mfc.md) y [serialización](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [Uso de CObject](../mfc/using-cobject.md)

