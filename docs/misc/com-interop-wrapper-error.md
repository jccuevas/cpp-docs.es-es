---
title: "COM Interop Wrapper Error | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotcopyassembly"
  - "Vs.refruntlbimp"
helpviewer_keywords: 
  - "COM Interop Wrapper dialog box"
ms.assetid: 9a9d6374-ee26-4dbc-9e34-e1d90f6254b4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop Wrapper Error
Este cuadro de mensaje se muestra cuando el sistema del proyecto no puede crear un contenedor de interoperabilidad COM para un componente determinado.  Common Language Runtime \(CLR\) requiere contenedores de interoperabilidad COM para administrar componentes COM y comunicarse con ellos.  Para obtener más información, consulte [Interoperabilidad COM en Visual Basic y Visual C\#](../Topic/COM%20Interoperability%20in%20.NET%20Framework%20Applications%20\(Visual%20Basic\).md).  
  
 Algunas causas frecuentes de error son:  
  
-   La biblioteca de tipos del componente no se ha registrado correctamente.  
  
-   No se ha encontrado un componente del que depende el componente que se debe ajustar.  
  
 En ambos casos, asegúrese de que el componente COM está correctamente instalado y registrado en la máquina, y reintente la operación.  
  
> [!TIP]
>  También puede buscar en el [sitio web de MSDN](http://go.microsoft.com/fwlink/?LinkId=3355) un contenedor de interoperabilidad COM que se haya publicado para el componente COM específico.  
  
> [!NOTE]
>  Los contenedores de interoperabilidad COM también se denominan en ocasiones "ensamblados de interoperabilidad primarios". Estos términos son sinónimos.  
  
## Vea también  
 [Espacios de nombres del modelo de componentes en Visual Studio](http://msdn.microsoft.com/es-es/705d0add-0707-44ba-a6de-637381d9c937)   
 [Component Authoring](../Topic/Component%20Authoring.md)   
 [Interoperabilidad COM](../Topic/COM%20Interop%20\(Visual%20Basic\).md)   
 [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md)   
 [Interoperabilidad COM en aplicaciones .NET Framework](../Topic/COM%20Interoperability%20in%20.NET%20Framework%20Applications%20\(Visual%20Basic\).md)