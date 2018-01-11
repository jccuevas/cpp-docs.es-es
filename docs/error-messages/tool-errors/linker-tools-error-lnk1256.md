---
title: Las herramientas del vinculador LNK1256 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- xml
- LNK1256
dev_langs: C++
helpviewer_keywords: LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbbb14e4f4fdef63b58bdef5ecafcfe0b045f412
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1256"></a>Error de las herramientas del vinculador LNK1256
Error de operación ALINK: razón  
  
 Una razón común para LNK1256 es un número de versión incorrecto para un ensamblado. El valor 65535 no está permitido en ninguna parte del número de versión del ensamblado. El intervalo válido para las versiones de ensamblado es 0 - 65534.  
  
 LNK1256 también puede producirse si ALINK no pudo encontrar el contenedor de claves nombrado. Eliminar el contenedor de claves y agregarlo de nuevo para el CSP de nombres seguros mediante [Sn.exe (herramienta de nombre seguro)](/dotnet/framework/tools/sn-exe-strong-name-tool).  
  
 Otra razón para el error LNK1256 es una discrepancia de versiones entre el vinculador y Alink.dll. Esto puede deberse a una instalación dañada de Visual Studio. Use **programas y características** en el Panel de Control de Windows para reparar o reinstalar Visual Studio.  
  
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