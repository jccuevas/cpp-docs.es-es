---
title: Especificar optimizaciones del compilador para un proyecto ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
dev_langs: C++
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b9b3d6b3fabe2a24a4b296709e835d07a63e441
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>Especificar optimizaciones del compilador para un proyecto ATL
De forma predeterminada, el [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md) genera clases nuevas con la macro ATL_NO_VTABLE, como se indica a continuación:  
  
```  
class ATL_NO_VTABLE CProjName  
{  
 ...  
};  
```  
  
 Después ATL define _ATL_NO_VTABLE como se indica a continuación:  
  
```  
#ifdef _ATL_DISABLE_NO_VTABLE  
 #define ATL_NO_VTABLE  
#else  
 #define ATL_NO_VTABLE __declspec(novtable)  
#endif  
```  
  
 Si no define _ATL_DISABLE_NO_VTABLE, la macro ATL_NO_VTABLE se expande a `declspec(novtable)`. Usar `declspec(novtable)`en una clase de declaración impide que el puntero vtable que se inicializa en el constructor de clase y el destructor. Cuando se compila el proyecto, el vinculador eliminará vtable y todas las funciones a la que señala la vtable.  
  
 Debe utilizar ATL_NO_VTABLE y, por consiguiente, `declspec(novtable)`, únicamente con clases base que no se puede crear directamente. No debe utilizar `declspec(novtable)` con la clase más derivada en el proyecto, dado que esta clase (normalmente [CComObject](../../atl/reference/ccomobject-class.md), [CComAggObject](../../atl/reference/ccomaggobject-class.md), o [CComPolyObject](../../atl/reference/ccompolyobject-class.md)) Inicializa el puntero vtable para el proyecto.  
  
 No debe llamar a funciones virtuales desde el constructor de cualquier objeto que usa `declspec(novtable)`. Debe mover esas llamadas a la [FinalConstruct](ccomobjectrootex-class.md#finalconstruct) método.  

  
 Si no está seguro de si debe usar el `declspec(novtable)` modificador, puede quitar la macro ATL_NO_VTABLE de cualquier definición de clase o puede deshabilitarla globalmente especificando  
  
```  
#define _ATL_DISABLE_NO_VTABLE  
```  
  
 en stdafx.h, antes de todos los demás ATL, archivos de encabezado se incluyen.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)   
 [Tipos de proyecto de Visual C++](../../ide/visual-cpp-project-types.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programar con ATL y el código de tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [novtable](../../cpp/novtable.md)   
 [Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)

