---
title: Palabras clave contextuales (extensiones de componentes de C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal_CPP
dev_langs:
- C++
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ceea3242087d89b511f6309003efe38d155735d2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="context-sensitive-keywords--c-component-extensions"></a>Palabras clave contextuales (Extensiones de componentes de C++)
*Palabras clave contextuales* son elementos del lenguaje que solo se reconocen en contextos concretos. Fuera del contexto concreto, una palabra clave contextual puede ser un símbolo definido por el usuario.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 **Comentarios**  
  
 A continuación se muestra una lista de palabras clave contextuales:  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [delegate](../windows/delegate-cpp-component-extensions.md)  
  
-   [event](../windows/event-cpp-component-extensions.md)  
  
-   [finally](../dotnet/finally.md)  
  
-   [for each, in](../dotnet/for-each-in.md)  
  
-   [initonly](../dotnet/initonly-cpp-cli.md)  
  
-   `internal`   
  
-   [Literal](../windows/literal-cpp-component-extensions.md)  
  
-   [override](../windows/override-cpp-component-extensions.md)  
  
-   [propiedad](../windows/property-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   `where` (parte de [genéricos](../windows/generics-cpp-component-extensions.md))  
  
 Por motivos de legibilidad, puede que desee limitar el uso de palabras clave contextuales como símbolos definidos por el usuario.  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 **Comentarios**  
  
 (No hay ninguna observación específica de la plataforma para esta característica).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Comentarios**  
  
 (No hay ninguna observación específica de la plataforma para esta característica).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra que, en el contexto adecuado, la palabra clave contextual `property` se puede utilizar para definir una propiedad y una variable.  
  
```  
// context_sensitive_keywords.cpp  
// compile with: /clr  
public ref class C {  
   int MyInt;  
public:  
   C() : MyInt(99) {}  
  
   property int Property_Block {   // context-sensitive keyword  
      int get() { return MyInt; }  
   }  
};  
  
int main() {  
   int property = 0;               // variable name  
   C ^ MyC = gcnew C();  
   property = MyC->Property_Block;  
   System::Console::WriteLine(++property);  
}  
```  
  
 **Salida**  
  
```Output  
100  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)