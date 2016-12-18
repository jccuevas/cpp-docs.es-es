---
title: "Advertencia de las herramientas del vinculador LNK4227 | Microsoft Docs"
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
  - "LNK4227"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4227"
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4227
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

advertencia de operación de metadatos \(HRESULT\) : mensaje\_de\_advertencia  
  
 El vinculador ha detectado diferencias de metadatos durante la combinación:  
  
-   Uno o más ensamblados a los que se hace referencia con el ensamblado que se está compilando actualmente.  
  
-   Uno o más archivos de código fuente en una compilación.  
  
 Por ejemplo, es posible que se produzca LNK4227 si se tienen dos funciones globales con el mismo nombre pero la información de los parámetros se declara de forma diferente \(las declaraciones no son coherentes en todos los elementos que se van a compilar\).  Utilice ildasm.exe \/TEXT \/METADATA `object_file` en cada archivo .obj y verá las diferencias entre los tipos.  
  
 La advertencia LNK4227 también informa de problemas que se originan con otra herramienta.  Por ejemplo, al.exe; vea [Errores y advertencias de la herramienta Al.exe](http://msdn.microsoft.com/es-es/7f125d49-0a03-47a6-9ba9-d61a679a7d4b).  
  
 Los problemas con metadatos deben resolverse para poder evitar esta advertencia.  
  
 Por ejemplo, la advertencia LNK4227 se genera cuando un ensamblado al que se hace referencia se firma de forma distinta al ensamblado que hace referencia al mismo.  
  
 El código siguiente genera el error LNK4227:  
  
```  
// LNK4227.cpp  
// compile with: /clr  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 y, a continuación,  
  
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
  
 El código siguiente genera el error LNK4227:  
  
```  
// LNK4227c.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 y, a continuación,  
  
```  
// LNK4227d.cpp  
// compile with: /clr:oldSyntax LNK4227c.cpp /FeLNK4227d.exe  
#using <mscorlib.dll>  
using namespace System::Reflection;  
using namespace System::Runtime::CompilerServices;  
  
[assembly:AssemblyDelaySignAttribute(true)];  
  
__gc class MyClass  
{  
};  
```  
  
 También se puede generar LNK4227 cuando se pasan números de versión con un formato equivocado a los atributos de ensamblado.  La notación con '\*' es específica de AssemblyVersionAttribute.  Para resolver esta advertencia, utilice sólo números en los atributos de versión que no sean AssemblyVersionAttribute.  
  
 El código siguiente genera el error LNK4227:  
  
```  
// LNK4227e.cpp  
// compile with: /clr /LD /W1  
using namespace System::Reflection;  
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK  
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227  
// try the following line instead  
// [assembly:AssemblyFileVersionAttribute("2.3")];  
```