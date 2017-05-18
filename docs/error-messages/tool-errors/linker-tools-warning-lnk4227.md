---
title: Las herramientas del vinculador LNK4227 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4227
dev_langs:
- C++
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: ee566318c7d19159f9a2c084d348b5010a65e2de
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-warning-lnk4227"></a>Advertencia de las herramientas del vinculador LNK4227
Advertencia de operación de metadatos (HRESULT): mensaje_de_advertencia  
  
El vinculador ha detectado diferencias de metadatos al combinar:  
  
-   Uno o más ensamblados que se hace referencia al ensamblado que se está generando actualmente.  
  
-   Uno o más archivos de código fuente una compilación.  
  
Por ejemplo, puede deberse LNK4227 si dispone de dos funciones globales con el mismo nombre pero con información de parámetros que se declaran de forma diferente (las declaraciones no son coherentes en todos los elementos). Utilice ildasm.exe /TEXT /METADATA `object_file` en cada .obj archivo y debería ver cómo difieren los tipos.  
  
LNK4227 también informa de los problemas que se originan con otra herramienta. Por ejemplo, al.exe; consulte [Al.exe herramienta errores y advertencias](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b).  
  
Los problemas con metadatos deben corregirse para resolver la advertencia.  
  
Por ejemplo, LNK4227 se genera cuando un ensamblado se firmó distinta al ensamblado que hace referencia a él.  
  
El ejemplo siguiente genera la advertencia LNK4227:  
  
```  
// LNK4227.cpp  
// compile with: /clr  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 Y entonces  
  
```  
// LNK4227b.cpp  
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe  
using namespace System::Reflection;  
using namespace System::Runtime::CompilerServices;  
  
[assembly:AssemblyDelaySignAttribute(true)];  
// Try the following line instead  
// [assembly:AssemblyDelaySignAttribute(false)];  
  
ref class MyClass  
{  
};  
```  
  
También se puede generar LNK4227 cuando se pasan números de versión en el formato equivocado a los atributos de ensamblado.  El ' *' notación es específica de AssemblyVersionAttribute.  Para resolver esta advertencia, utilice sólo números en los atributos de versión que no sean AssemblyVersionAttribute.  
  
El ejemplo siguiente genera la advertencia LNK4227:  
  
```  
// LNK4227e.cpp  
// compile with: /clr /LD /W1  
using namespace System::Reflection;  
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK  
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227  
// try the following line instead  
// [assembly:AssemblyFileVersionAttribute("2.3")];  
```
