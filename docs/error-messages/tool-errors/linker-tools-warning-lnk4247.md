---
title: "Advertencia de las herramientas del vinculador LNK4247 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4247"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4247"
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4247
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el punto de entrada 'nombre\_representativo\_de\_función' ya tiene un atributo de subproceso; 'atributo' omitido  
  
 Un punto de entrada, especificado con [\/ENTRY \(Símbolo de punto de entrada\)](../../build/reference/entry-entry-point-symbol.md), tenía un atributo de subprocesamiento, pero también se especificó [\/CLRTHREADATTRIBUTE \(Establecer el atributo de subproceso de CLR\)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md), con un modelo de subprocesos diferente.  
  
 El vinculador omitió el valor especificado con \/CLRTHREADATTRIBUTE.  
  
 Para solucionarlo:  
  
-   Quite \/CLRTHREADATTRIBUTE de su compilación.  
  
-   Quite el atributo de su archivo de código fuente.  
  
-   Quite el atributo del código fuente y \/CLRTHREADATTRIBUTE de la compilación, y acepte el modelo de subprocesos de CLR predeterminado.  
  
-   Cambie el valor pasado a \/CLRTHREADATTRIBUTE, de modo que no esté en conflicto con el atributo del código fuente.  
  
-   Cambie el atributo del código fuente, de modo que no esté en conflicto con el valor pasado a \/CLRTHREADATTRIBUTE.  
  
 En el siguiente ejemplo, se genera la advertencia LNK4247  
  
```  
// LNK4247.cpp  
// compile with: /clr /c  
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console  
 [System::MTAThreadAttribute]  
void functionTitle (){}  
```