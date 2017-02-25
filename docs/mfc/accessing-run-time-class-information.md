---
title: "Acceso a la informaci&#243;n de clases en tiempo de ejecuci&#243;n | Microsoft Docs"
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
  - "clases [C++], información de clases en tiempo de ejecución"
  - "CObject (clase), obtener acceso a la información de clases en tiempo de ejecución"
  - "CObject (clase), y RTTI"
  - "CObject (clase), utilizar el método IsKindOf"
  - "CObject (clase), utilizar la macro RUNTIME_CLASS"
  - "IsKindOf (método)"
  - "RTTI (opción del compilador)"
  - "tiempo de ejecución"
  - "tiempo de ejecución, información de clases"
  - "clase en tiempo de ejecución"
  - "clase en tiempo de ejecución, obtener acceso a la información"
  - "RUNTIME_CLASS (macro)"
  - "RUNTIME_CLASS (macro), utilizar"
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Acceso a la informaci&#243;n de clases en tiempo de ejecuci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo obtener acceso a información de clase de un objeto en tiempo de ejecución.  
  
> [!NOTE]
>  MFC no utiliza la compatibilidad de [Información en tiempo de ejecución](../cpp/run-time-type-information.md) \(RTTI\) introducido en Visual C\+\+ 4,0.  
  
 Si ha derivado una clase de [CObject](../mfc/reference/cobject-class.md) y ha utilizado el \_**dinámico** y `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE`de **declare**, o macros de `DECLARE_SERIAL` y de `IMPLEMENT_SERIAL` explicadas en el caso [Derivar de una clase de CObject](../mfc/deriving-a-class-from-cobject.md), la clase de `CObject` tiene la capacidad de determinar la clase exacta de un objeto en tiempo de ejecución.  
  
 Esta capacidad es más útil cuando la comprobación de tipo adicional de los argumentos de la función es necesaria y cuando debe escribir el código especial basado en la clase de un objeto.  Sin embargo, este procedimiento no suele ser recomendable porque duplica la funcionalidad de funciones virtuales.  
  
 La función `IsKindOf` miembro de `CObject` se puede utilizar para determinar si un determinado objeto pertenece a una clase especificada o si se deriva de una clase concreta.  El argumento en `IsKindOf` es un objeto de `CRuntimeClass` , que se puede obtener mediante la macro de `RUNTIME_CLASS` con el nombre de clase.  
  
### Para utilizar la macro de RUNTIME\_CLASS  
  
1.  Utilice `RUNTIME_CLASS` con el nombre de clase, como se muestra aquí para la clase `CObject`:  
  
     [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/CPP/accessing-run-time-class-information_1.cpp)]  
  
 Necesitará raramente tener acceso a la clase en tiempo de ejecución directamente.  Un uso común es pasar el objeto de clase en tiempo de ejecución a la función de `IsKindOf` , como se muestra en el procedimiento siguiente.  Las pruebas de función de `IsKindOf` un objeto para ver si pertenece a una clase determinada.  
  
#### Para utilizar la función IsKindOf  
  
1.  Asegúrese de que la clase tenga compatibilidad con la clase en tiempo de ejecución.  Es decir, la clase debe haberse derivado directa o indirectamente de `CObject` y utilizó \_**dinámico** y `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE`de **declare**, o macros de `DECLARE_SERIAL` y de `IMPLEMENT_SERIAL` explicadas en el caso [Derivar de una clase de CObject](../mfc/deriving-a-class-from-cobject.md).  
  
2.  Llame a la función miembro de `IsKindOf` para los objetos de esa clase, mediante la macro de `RUNTIME_CLASS` para generar el argumento de `CRuntimeClass` , como se muestra aquí:  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/CPP/accessing-run-time-class-information_2.h)]  
  
     [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/CPP/accessing-run-time-class-information_3.cpp)]  
  
    > [!NOTE]
    >  IsKindOf devuelve **VERDADERO** si el objeto es un miembro de la clase especificada o de una clase derivada de la clase especificada.  `IsKindOf` no admite la herencia múltiple o clases base virtuales, aunque puede utilizar la herencia múltiple de clases derivadas de la Microsoft foundation class en caso necesario.  
  
 Un uso de la información de la clase en tiempo de ejecución está en la creación dinámica de objetos.  Este proceso se describe en el artículo [Creación de objetos dinámica](../mfc/dynamic-object-creation.md).  
  
 Para obtener información más detallada sobre la serialización y la clase en tiempo de ejecución, vea los artículos [Archivos en MFC](../mfc/files-in-mfc.md) y [Serialización](../mfc/serialization-in-mfc.md).  
  
## Vea también  
 [Usar CObject](../mfc/using-cobject.md)