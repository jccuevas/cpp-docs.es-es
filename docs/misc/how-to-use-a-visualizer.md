---
title: "C&#243;mo: Utilizar un visualizador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dataviewer"
  - "vs.debug.stringviewer"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, visualizadores"
  - "visualizadores, acerca de los visualizadores"
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
caps.handback.revision: 37
ms.author: "susanno"
manager: "douge"
---
# C&#243;mo: Utilizar un visualizador
Puede utilizar un visualizador para mostrar el contenido de una variable o un objeto de manera significativa para el tipo de datos.  Puede usar los visualizadores de **Información sobre datos**, una ventana **Inspección**, la ventana **Automático** o la ventana **Variables locales**.  
  
 Los visualizadores no se admiten en .NET Compact Framework.  
  
> [!NOTE]
>  En las aplicaciones de la **Tienda**, solo se admiten los visualizadores de texto estándar, HTML, XML y JSON.  No se admiten los visualizadores personalizados \(creados por el usuario\).  
  
### Para abrir un visualizador  
  
1.  Haga clic en el icono de lupa que aparece junto a un nombre de variable en **Información sobre datos**, una ventana **Inspección** o en las ventanas **Automático**, **Variables locales** o **Inspección rápida**.  
  
     Se mostrará una lista de visualizadores.  
  
2.  Haga clic en el visualizador que desee usar.  
  
### Para utilizar un visualizador para el código administrado durante la depuración remota  
  
-   Copie el archivo DLL del visualizador en el equipo remoto antes de iniciar la sesión de depuración.  
  
     La ruta de acceso al archivo DLL debe ser la misma en el equipo remoto y en el equipo local.  Esta ruta de acceso puede ser cualquiera de las siguientes ubicaciones:  
  
     *Ruta de acceso de instalación de Visual Studio*`\Common7\Packages\Debugger\Visualizers`  
  
     O bien  
  
     `My Documents\Visual Studio 2010\Visualizers`*Versión de Visual Studio*`\Visualizers`  
  
## Vea también  
 [Visualizadores](../Topic/Create%20Custom%20Visualizers%20of%20Data.md)   
 [Cómo: Instalar un visualizador](../Topic/How%20to:%20Install%20a%20Visualizer.md)   
 [Cómo: Escribir un visualizador](../Topic/How%20to:%20Write%20a%20Visualizer.md)   
 [Ver valores de datos en sugerencias de datos](../Topic/View%20data%20values%20in%20Data%20Tips%20%20in%20the%20code%20editor.md)