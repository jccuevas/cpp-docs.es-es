---
title: "Hay una p&#233;rdida de memoria en el archivo DLL est&#225;ndar, pero no encuentro el problema en el c&#243;digo. &#191;C&#243;mo se puede localizar la p&#233;rdida de memoria? | Microsoft Docs"
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
  - "DLL [C++], pérdidas de memoria"
  - "pérdidas de memoria [C++], DLL"
ms.assetid: a5d76573-b567-4b6a-8303-dafeeed9204d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Hay una p&#233;rdida de memoria en el archivo DLL est&#225;ndar, pero no encuentro el problema en el c&#243;digo. &#191;C&#243;mo se puede localizar la p&#233;rdida de memoria?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una causa posible de la pérdida de memoria es que MFC crea objetos temporales que se utilizan dentro de funciones de controlador de mensajes.  En archivos DLL estándar, MFC no libera automáticamente la memoria asignada para estos objetos.  Para obtener más información, vea [La administración de memoria y el montón de depuración](http://msdn.microsoft.com/es-es/34dc6ef6-31c9-460e-a2a7-15e7f8e3334b) o el artículo "Cleaning Up Temporary MFC Objects in \_USRDLL DLLs" \(Q105286\) de Knowledge Base.  
  
 Tenga en cuenta que en la documentación de Visual C\+\+ ya no se utiliza el término USRDLL.  Un archivo DLL estándar vinculado estáticamente a MFC tiene las mismas características que el antiguo archivo USRDLL.  El consejo del artículo de Knowledge Base también se aplica a archivos DLL estándar vinculados dinámicamente a MFC.  La información del articulo anterior de Knowledge Base se aplica a archivos DLL estándar vinculados estáticamente a MFC y a archivos DLL estándar vinculados dinámicamente a MFC.  
  
## Vea también  
 [Preguntas más frecuentes sobre archivos DLL](../build/dll-frequently-asked-questions.md)