---
title: Las herramientas del vinculador LNK4247 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4247
dev_langs: C++
helpviewer_keywords: LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 517605993199942f863faa78e14a022529214a64
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4247"></a>Advertencia de las herramientas del vinculador LNK4247
punto de entrada 'nombre_representativo_de_función' ya tiene un atributo de subproceso; 'atributo' omitido  
  
 Un punto de entrada especificado con [/ENTRY (símbolo de punto de entrada)](../../build/reference/entry-entry-point-symbol.md), tenía un atributo de subprocesamiento, pero [/CLRTHREADATTRIBUTE (Set CLR Thread Attribute)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) también se especificó, con un modelo de subprocesos diferentes.  
  
 El vinculador omitió el valor especificado con/CLRTHREADATTRIBUTE.  
  
 Para resolver esta advertencia:  
  
-   Quitar/CLRTHREADATTRIBUTE de la compilación.  
  
-   Quite el atributo de archivo de código fuente.  
  
-   Elimine el atributo de origen y/CLRTHREADATTRIBUTE de la compilación y acepte el modelo de subprocesos de CLR de forma predeterminada.  
  
-   Cambie el valor pasado a/CLRTHREADATTRIBUTE, de modo que lo está de acuerdo con el atributo de origen.  
  
-   Cambie el atributo de origen, de modo que lo está de acuerdo con el valor pasado a/CLRTHREADATTRIBUTE.  
  
 El ejemplo siguiente genera la advertencia LNK4247  
  
```  
// LNK4247.cpp  
// compile with: /clr /c  
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console  
 [System::MTAThreadAttribute]  
void functionTitle (){}  
```