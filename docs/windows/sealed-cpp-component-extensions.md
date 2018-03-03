---
title: sealed (extensiones de componentes de C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sealed_cpp
- sealed
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb8a8b7ea695d878235898a8741adf04ba91748c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sealed--c-component-extensions"></a>sealed (Extensiones de componentes de C++)
`sealed` es una palabra clave contextual para las clases ref que indica que no se puede reemplazar un miembro virtual o que no se puede usar un tipo como tipo base.  
  
> [!NOTE]
>  El ISO C ++ 11 estándar lenguaje tiene la [final](../cpp/final-specifier.md) palabra clave, que se admite en Visual Studio. Use `final` en clases estándar y `sealed` en las clases ref.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
  
## <a name="syntax"></a>Sintaxis
  
```  
ref class identifier sealed {...};  
virtual return-type identifier() sealed {...};  
```  
  
### <a name="parameters"></a>Parámetros  
  
 *identifier*  
 Nombre de la función o clase.  
  
 *tipo de valor devuelto*  
 Tipo devuelto por una función.  
  
## <a name="remarks"></a>Comentarios  
  
 En el primer ejemplo de sintaxis, una clase está sellada. En el segundo ejemplo, una función virtual está sellada.  
  
 El `sealed` palabra clave es válida para destinos nativos y también para el tiempo de ejecución de Windows y common language runtime (CLR). Para obtener más información, consulte [especificadores de invalidación y compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
 Puede detectar en tiempo de compilación si un tipo está sellado usando el `__is_sealed(type)` rasgo de tipo. Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 `sealed` es una palabra clave contextual.  Para obtener más información, consulte [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 Vea [clases y structs Ref](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 (No hay notas para esta característica de lenguaje que solo se apliquen a Common Language Runtime).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 Este ejemplo de código siguiente muestra el efecto de `sealed` en un miembro virtual.  
  
```cpp  
// sealed_keyword.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
   virtual void g();  
};  
  
ref class X : I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
  
   virtual void g() sealed {  
      System::Console::WriteLine("X::f override of I1::g");  
   }  
};  
  
ref class Y : public X {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("Y::f override of I1::f");  
   }  
  
   /*  
   // the following override generates a compiler error  
   virtual void g() override {  
      System::Console::WriteLine("Y::g override of I1::g");  
   }    
   */  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
   MyI -> g();  
  
   I1 ^ MyI2 = gcnew Y;  
   MyI2 -> f();  
}  
```  
  
```Output  
X::f override of I1::f  
X::f override of I1::g  
Y::f override of I1::f  
```  
  
 En el ejemplo de código siguiente se muestra cómo marcar una clase como sellada.  
  
```cpp  
// sealed_keyword_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X sealed : I1 {  
public:  
   virtual void f() override {}  
};  
  
ref class Y : public X {   // C3246 base class X is sealed  
public:  
   virtual void f() override {}  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)