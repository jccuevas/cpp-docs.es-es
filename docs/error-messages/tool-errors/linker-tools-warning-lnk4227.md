---
title: Las herramientas del vinculador LNK4227 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4227
dev_langs:
- C++
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b56617ee355654dfbb198252ea37cdb344950cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302115"
---
# <a name="linker-tools-warning-lnk4227"></a>Advertencia de las herramientas del vinculador LNK4227  
  
> Advertencia de operación de metadatos (*HRESULT*): *mensaje_de_advertencia*  
  
El vinculador ha detectado diferencias de metadatos cuando se mezclan:  
  
-   Uno o más ensamblados que se hace referencia al ensamblado que se está generando actualmente.  
  
-   Uno o más archivos de código fuente una compilación.  
  
Por ejemplo, puede generarse LNK4227 si dispone de dos funciones globales con el mismo nombre pero con información de parámetros que se declaran de forma diferente (es decir, las declaraciones no son coherentes en todos los elementos). Use ildasm.exe /TEXT /METADATA *las diferencias entre* en cada archivo .obj para ver la diferencia entre los tipos.  
  
LNK4227 también se utiliza para informar de los problemas que se originan con otra herramienta. Busque el mensaje de advertencia para obtener más información.  
  
Deben solucionar los problemas con metadatos para resolver la advertencia.  
  
## <a name="example"></a>Ejemplo  
  
LNK4227 se genera cuando un ensamblado de referencia estaba firmado de forma diferente que el ensamblado que hace referencia a él.  
  
El ejemplo siguiente genera la advertencia LNK4227:  
  
```cpp  
// LNK4227.cpp  
// compile with: /clr  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 Y entonces  
  
```cpp  
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
  
## <a name="example"></a>Ejemplo  
  
También se puede generar LNK4227 cuando los números de versión en un formato incorrecto se pasan a los atributos de ensamblado.  El ' *' notación es específica de la `AssemblyVersionAttribute`.  Para resolver esta advertencia, utilice sólo números en los atributos de versión distinto de `AssemblyVersionAttribute`.  
  
El ejemplo siguiente genera la advertencia LNK4227:  
  
```cpp  
// LNK4227e.cpp  
// compile with: /clr /LD /W1  
using namespace System::Reflection;  
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK  
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227  
// try the following line instead  
// [assembly:AssemblyFileVersionAttribute("2.3")];  
```