---
title: ".SAFESEH | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ".SAFESEH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "registering functions as exception handlers"
  - "SAFESEH directive"
  - ".SAFESEH directive"
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .SAFESEH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Registra una función como controlador de excepciones estructurado.  
  
## Sintaxis  
  
```  
  
.SAFESEH identifier  
```  
  
## Comentarios  
 *el identificador* debe ser el identificador de [PROCEDURE](../../assembler/masm/proc.md) o un PROCEDURE definido localmente de [EXTRN](../../assembler/masm/extrn.md) .  [ETIQUETA](../../assembler/masm/label-masm.md) no está permitido.  La directiva de .SAFESEH requiere la opción de línea de comandos [\/safeseh](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml.exe.  
  
 Para obtener más información sobre controladores de excepciones estructurados, vea [\/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).  
  
 Por ejemplo, para registrar un controlador de excepciones seguro, cree un nuevo archivo de MASM \(como siguiente\), ensamblar con \/safeseh, y agregue a los objetos vinculados.  
  
```  
.386  
.model  flat  
MyHandler   proto  
.safeseh    MyHandler  
end  
```  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)