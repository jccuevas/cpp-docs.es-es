---
title: "/Zc:auto (Deducir tipo de variable) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Zc:auto"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc (opción del compilador) (C++)"
  - "Deducir tipo de variable (C++)"
  - "Zc (opción del compilador) (C++)"
  - "-Zc (opción del compilador) (C++)"
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /Zc:auto (Deducir tipo de variable)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La opción del compilador **\/Zc:auto\[\-\]** le indica al compilador cómo usar la [palabra clave auto](../../cpp/auto-keyword.md) para declarar variables.  Si especifica la opción predeterminada, **\/Zc:auto**, el compilador deducirá el tipo de la variable declarada a partir de su expresión de inicialización.  Si especifica  **\/Zc:auto\-**, el compilador asignará la variable a la clase de almacenamiento automático.  
  
## Sintaxis  
  
```  
/Zc:auto[-]  
```  
  
## Comentarios  
 El estándar C\+\+ define un significado original y uno revisado de la palabra clave `auto`.  Antes de [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)], la palabra clave declara una variable en la clase de almacenamiento automático: es decir, una variable que tiene una vigencia local.  Desde [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)], la palabra clave deduce el tipo de una variable a partir de la expresión de inicialización de la declaración. Utilice la opción del compilador **\/Zc:auto\[\-\]** para indicarle al compilador que use el significado original o el revisado de la palabra clave `auto`.  
  
 Si su forma de usar la palabra clave `auto` contradice la opción del compilador actual, el compilador emitirá el mensaje de diagnóstico correspondiente.  Para obtener más información, vea [auto \(Palabra clave\)](../../cpp/auto-keyword.md).  Para obtener más información sobre los problemas de conformidad con Visual C\+\+, vea [Comportamiento no estándar](../../cpp/nonstandard-behavior.md).  
  
### Para establecer esta opción del compilador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el nodo **Propiedades de configuración**.  
  
3.  Haga clic en el nodo **C\/C\+\+**.  
  
4.  Haga clic en el nodo **Línea de comandos**.  
  
5.  Agregue **\/Zc:auto** o **\/Zc:auto\-** al panel **Opciones adicionales:** .  
  
## Vea también  
 [\/Zc \(Ajuste\)](../../build/reference/zc-conformance.md)   
 [auto \(Palabra clave\)](../../cpp/auto-keyword.md)