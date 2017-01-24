---
title: "Error de las herramientas del vinculador LNK1256 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "xml"
  - "LNK1256"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1256"
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1256
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Error de operación ALINK: razón  
  
 Una razón común para LNK1256 es un número de versión incorrecto para un ensamblado.  El valor 65535 no está permitido en ninguna parte del número de versión del ensamblado.  El intervalo válido para las versiones de ensamblado es de 0 a 65534.  
  
 LNK1256 también puede producirse si ALINK no pudo encontrar el contenedor de claves nombrado.  Elimine el contenedor de claves y agréguelo otra vez al CSP de nombres seguros mediante [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).  
  
 Otra razón para el error LNK1256 es una discrepancia de versiones entre el vinculador y Alink.dll.  Esto puede deberse a una instalación dañada de Visual Studio.  Utilice **Programas y características** en el Panel de control de Windows para reparar o reinstalar Visual Studio.  
  
 En el siguiente ejemplo se genera el error LNK1256:  
  
```  
// LNK1256.cpp  
// compile with: /clr /LD  
// LNK1256 expected  
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];  
public class CMyClass {  
public:  
   int value;  
};  
```