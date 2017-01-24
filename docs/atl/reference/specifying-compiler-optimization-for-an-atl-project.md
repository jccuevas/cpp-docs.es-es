---
title: "Especificar optimizaciones del compilador para un proyecto ATL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.optimization"
  - "vc.appwiz.ATL.vtable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL projects, optimización del compilador"
  - "ATL_DISABLE_NO_VTABLE (macro)"
  - "ATL_NO_VTABLE (macro)"
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Especificar optimizaciones del compilador para un proyecto ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

De manera predeterminada, el [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md) genera clases nuevas con la macro ATL\_NO\_VTABLE, como se indica a continuación:  
  
```  
class ATL_NO_VTABLE CProjName  
{  
   ...  
};  
```  
  
 Después ATL define \_ATL\_NO\_VTABLE de la manera siguiente:  
  
```  
#ifdef _ATL_DISABLE_NO_VTABLE  
   #define ATL_NO_VTABLE  
#else  
   #define ATL_NO_VTABLE __declspec(novtable)  
#endif  
```  
  
 Si no define \_ATL\_DISABLE\_NO\_VTABLE, la macro ATL\_NO\_VTABLE se expande a `declspec(novtable)`.  Si se utiliza `declspec(novtable)` en una declaración de clase, se evita la inicialización del puntero vtable en el constructor y el destructor de clase.  Cuando compile el proyecto, el vinculador eliminará vtable y todas las funciones a las que apunte vtable.  
  
 Debe utilizar ATL\_NO\_VTABLE y, en consecuencia, `declspec(novtable)`, únicamente con clases base que no se puedan crear directamente.  No debe utilizar `declspec(novtable)` con la clase más derivada del proyecto, ya que esta clase \(normalmente [CComObject](../../atl/reference/ccomobject-class.md), [CComAggObject](../../atl/reference/ccomaggobject-class.md) o [CComPolyObject](../../atl/reference/ccompolyobject-class.md)\) inicializa el puntero vtable para el proyecto.  
  
 No debe llamar a funciones virtuales desde el constructor de un objeto que utilice `declspec(novtable)`.  Debe mover esas llamadas al método [FinalConstruct](../Topic/CComObjectRootEx::FinalConstruct.md).  
  
 Si no está seguro de si debe utilizar el modificador `declspec(novtable)`, puede quitar la macro ATL\_NO\_VTABLE de cualquier definición de clase o puede deshabilitarla globalmente especificando  
  
```  
#define _ATL_DISABLE_NO_VTABLE  
```  
  
 en stdafx.h, antes de incluir los demás archivos de encabezado ATL.  
  
## Vea también  
 [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)   
 [Tipos de proyecto de Visual C\+\+](../../ide/visual-cpp-project-types.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [novtable](../../cpp/novtable.md)   
 [Configuraciones predeterminadas de un proyecto ATL](../../atl/reference/default-atl-project-configurations.md)