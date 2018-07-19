---
title: Plataforma, predeterminado y cli espacios de nombres (extensiones de componentes de C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- lang
- cli
dev_langs:
- C++
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b466a94aba9f19907a5438a8b8e623d65aa0ac2d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880757"
---
# <a name="platform-default-and-cli-namespaces--c-component-extensions"></a>Espacios de nombres de plataforma, predeterminado y CLI (Extensiones de componentes de C++)
Un espacio de nombres califica los nombres de los elementos de lenguaje de modo que no entren en conflicto con nombres que por lo demás son idénticos en otra parte del código fuente. Por ejemplo, un conflicto de nombres puede evitar que el compilador reconozca [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md). El compilador utiliza los espacios de nombres, pero no se conservan en el ensamblado compilado.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 Visual C++ proporciona un espacio de nombres predeterminado para el proyecto cuando se crea. Puede cambiar manualmente el espacio de nombres, aunque en tiempo de ejecución de Windows el nombre del archivo .winmd debe coincidir con el nombre del espacio de nombres raíz.  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 Para obtener más información, consulte [visibilidad de espacios de nombres y el tipo (C++ / CX)](http://msdn.microsoft.com/library/windows/apps/hh969551.aspx).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Sintaxis**  
  
```  
using namespace cli;  
```  
  
 **Comentarios**  
  
 C++ / CLI admite el `cli` espacio de nombres. Cuando se compila con **/CLR**, el `using` instrucción en la sección sintaxis está implícita.  
  
 Las características de lenguaje siguientes están en el espacio de nombres `cli`:  
  
-   [Matrices](../windows/arrays-cpp-component-extensions.md)  
  
-   [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)  
  
-   [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md)  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se demuestra que se puede usar un símbolo en el espacio de nombres `cli` como símbolo definido por el usuario en el código.  Sin embargo, después de realizar esta acción, deberá calificar explícita o implícitamente las referencias al elemento de lenguaje `cli` del mismo nombre.  
  
```  
// cli_namespace.cpp  
// compile with: /clr  
using namespace cli;  
int main() {  
   array<int> ^ MyArray = gcnew array<int>(100);  
   int array = 0;  
  
   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062  
  
   // OK  
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);  
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)