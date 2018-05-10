---
title: __identifier (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
dev_langs:
- C++
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a96363fcfbc753e727c6cbb6a5efbbb5606b6c40
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)
Habilita el uso de palabras clave de Visual C++ como identificadores.  
  
## <a name="all-platforms"></a>Todas las plataformas  
**Sintaxis**  
  
```  
__identifier(  
Visual_C++_keyword  
)  
  
```  
  
**Comentarios**  
  
El uso de la `__identifier` palabra clave para los identificadores que no son palabras clave está permitido, pero no se recomienda por cuestión de estilo.  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
### <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 En el ejemplo siguiente, una clase denominada `template` se crea en C# y se distribuye como un archivo DLL. En el programa de Visual C++ que usa el `template` (clase), el `__identifier` palabra clave oculta el hecho de que `template` es una palabra clave de C++ estándar.  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /ZW  
#using <identifier_template.dll>  
int main() {  
   __identifier(template)^ pTemplate = ref new __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Comentarios**  
  
 El `__identifier` palabra clave es válida con el **/CLR** opción del compilador.  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 En el ejemplo siguiente, una clase denominada `template` se crea en C# y se distribuye como un archivo DLL. En el programa de Visual C++ que usa el `template` (clase), el `__identifier` palabra clave oculta el hecho de que `template` es una palabra clave de C++ estándar.  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /clr  
#using <identifier_template.dll>  
  
int main() {  
   __identifier(template) ^pTemplate = gcnew __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)   
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)