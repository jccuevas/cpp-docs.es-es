---
title: "C&#243;mo: Compilar aplicaciones aisladas que utilicen componentes COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones aisladas [C++]"
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C&#243;mo: Compilar aplicaciones aisladas que utilicen componentes COM
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las aplicaciones aisladas son aquéllas que tienen manifiestos integrados en el programa.  Puede crear aplicaciones aisladas para utilizar componentes COM.  
  
### Para agregar referencias COM a manifiestos de aplicaciones aisladas  
  
1.  Abra las páginas de propiedades de proyecto correspondientes a la aplicación aislada.  
  
2.  Expanda el nodo **Propiedades de configuración** y, a continuación, expanda el nodo **Herramienta Manifiesto**.  
  
3.  Seleccione la página de propiedades **COM aislado** y, a continuación, establezca la propiedad **Nombre de archivo del componente** en el nombre del componente COM que la aplicación aislada deba utilizar.  
  
4.  Haga clic en **Aceptar**.  
  
### Para integrar manifiestos en aplicaciones aisladas  
  
1.  Abra las páginas de propiedades de proyecto correspondientes a la aplicación aislada.  
  
2.  Expanda el nodo **Propiedades de configuración** y, a continuación, expanda el nodo **Herramienta Manifiesto**.  
  
3.  Seleccione la página de propiedades **Entrada y salida** y, a continuación, establezca la propiedad **Incrustar manifiesto** en **Sí**.  
  
4.  Haga clic en **Aceptar**.  
  
5.  Compile la solución.  
  
## Vea también  
 [Aplicaciones aisladas](http://msdn.microsoft.com/library/aa375190)   
 [Ensamblados en paralelo](_win32_side_by_side_assemblies)