---
title: "C&#243;mo: Crear componentes COM de registro gratuito | Microsoft Docs"
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
  - "componentes COM, sin registro"
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# C&#243;mo: Crear componentes COM de registro gratuito
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los componentes COM sin registro son componentes COM que tienen los manifiestos integrados en los archivos DLL.  
  
### Para crear manifiestos en los componentes COM  
  
1.  Abra las páginas de propiedades de proyecto correspondientes al componente COM.  
  
2.  Expanda el nodo **Propiedades de configuración** y, a continuación, expanda el nodo **Herramienta Manifiesto**.  
  
3.  Seleccione la página de propiedades **Entrada y salida** y, a continuación, establezca la propiedad **Incrustar manifiesto** en **Sí**.  
  
4.  Haga clic en **Aceptar**.  
  
5.  Compile la solución.  
  
## Vea también  
 [Aplicaciones aisladas](http://msdn.microsoft.com/library/aa375190)   
 [Ensamblados en paralelo](_win32_side_by_side_assemblies)   
 [Cómo: Compilar aplicaciones aisladas que utilicen componentes COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)