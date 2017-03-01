---
title: Especificar optimizaciones del compilador para un proyecto ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
dev_langs:
- C++
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: abdad4367e75c1971ba5d11af1a60992d1bb3dd4
ms.lasthandoff: 02/24/2017

---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>Especificar optimizaciones del compilador para un proyecto ATL
De forma predeterminada, el [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md) genera clases nuevas con la macro ATL_NO_VTABLE, como sigue:  
  
```  
class ATL_NO_VTABLE CProjName  
{  
 ...  
};  
```  
  
 Después ATL define _ATL_NO_VTABLE como sigue:  
  
```  
#ifdef _ATL_DISABLE_NO_VTABLE  
 #define ATL_NO_VTABLE  
#else  
 #define ATL_NO_VTABLE __declspec(novtable)  
#endif  
```  
  
 Si no define _ATL_DISABLE_NO_VTABLE, la macro ATL_NO_VTABLE se expande a `declspec(novtable)`. Mediante `declspec(novtable)`en una clase de declaración impide que el puntero vtable que se inicializa en el constructor de clase y el destructor. Al compilar el proyecto, el vinculador eliminará vtable y todas las funciones a la que señala la vtable.  
  
 Debe utilizar ATL_NO_VTABLE y por consiguiente `declspec(novtable)`, únicamente con clases base que no se puede crear directamente. No debe utilizar `declspec(novtable)` con la clase más derivada del proyecto, ya que esta clase (normalmente [CComObject](../../atl/reference/ccomobject-class.md), [CComAggObject](../../atl/reference/ccomaggobject-class.md), o [CComPolyObject](../../atl/reference/ccompolyobject-class.md)) inicializa el puntero vtable para el proyecto.  
  
 No debe llamar a funciones virtuales desde el constructor de cualquier objeto que usa `declspec(novtable)`. Debe mover esas llamadas a la [FinalConstruct](ccomobjectrootex-class.md#finalconstruct) método.  

  
 Si no está seguro de si debe utilizar el `declspec(novtable)` modificador, puede quitar la macro ATL_NO_VTABLE de cualquier definición de clase o puede deshabilitarla globalmente especificando  
  
```  
#define _ATL_DISABLE_NO_VTABLE  
```  
  
 en stdafx.h, antes de todos los demás ATL, archivos de encabezado se incluyen.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)   
 [Tipos de proyecto de Visual C++](../../ide/visual-cpp-project-types.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programar con ATL y el código de tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Fundamentos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [novtable](../../cpp/novtable.md)   
 [Configuraciones predeterminadas de proyecto ATL](../../atl/reference/default-atl-project-configurations.md)


