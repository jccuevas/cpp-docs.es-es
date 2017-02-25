---
title: "Modificar un objeto ATL para que no se pueda crear | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.objects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL projects, objetos que no se pueden crear"
  - "objetos ATL que no se pueden crear"
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Modificar un objeto ATL para que no se pueda crear
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede cambiar los atributos de un objeto COM basado en ATL de forma que un cliente no pueda crear directamente el objeto.  En este caso, el objeto se devolvería a través de una llamada a un método de otro objeto, en lugar de crearse directamente.  
  
### Para establecer que no se pueda crear un objeto  
  
1.  Quite la macro [OBJECT\_ENTRY\_AUTO](../Topic/OBJECT_ENTRY_AUTO.md) para el objeto.  Si desea establecer que no se pueda crear el objeto, pero sin impedir que se pueda registrar el control, reemplace OBJECT\_ENTRY\_AUTO por [OBJECT\_ENTRY\_NON\_CREATEABLE\_EX\_AUTO](../Topic/OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO.md).  
  
2.  Agregue el atributo [noncreatable](../../windows/noncreatable.md) a la coclase del archivo .idl.  Por ejemplo:  
  
    ```  
    [  
       uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851),  
       helpstring("MyObject"),  
      noncreatable  
    ]  
    coclass MyObject  
    {  
       [default] interface IMyInterface;  
    }  
    ```  
  
## Vea también  
 [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)   
 [Tipos de proyecto de Visual C\+\+](../../ide/visual-cpp-project-types.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [Configuraciones predeterminadas de un proyecto ATL](../../atl/reference/default-atl-project-configurations.md)