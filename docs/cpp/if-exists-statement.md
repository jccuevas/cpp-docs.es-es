---
title: "__if_exists (instrucción) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __if_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 3d0eaa00abb1f833ef491fc27bfee01790776edb
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="ifexists-statement"></a>__if_exists (Instrucción)
La instrucción `__if_exists` prueba si existe el identificador especificado. Si el identificador existe, se ejecuta el bloque de instrucción especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__if_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`identifier`|El identificador cuya existencia se desea probar.|  
|`statements`|Una o más instrucciones que se ejecutarán si `identifier` existe.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!CAUTION]
>  Para obtener los resultados más confiables, conviene utilizar la instrucción `__if_exists` con las restricciones siguientes.  
  
-   Aplique la instrucción `__if_exists` solo a tipos simples y no a plantillas.  
  
-   Aplique la instrucción `__if_exists` a identificadores tanto dentro como fuera de una clase. No aplique la instrucción `__if_exists` a variables locales.  
  
-   Utilice la instrucción `__if_exists` solo en el cuerpo de una función. Fuera del cuerpo de una función, la instrucción `__if_exists` solo puede probar tipos totalmente definidos.  
  
-   Cuando se prueban funciones sobrecargadas, no se puede probar una forma específica de la sobrecarga.  
  
 El complemento a la `__if_exists` instrucción es la [__if_not_exists](../cpp/if-not-exists-statement.md) instrucción.  
  
## <a name="example"></a>Ejemplo  
 Observe que este ejemplo utiliza plantillas, lo que no se recomienda.  
  
```  
// the__if_exists_statement.cpp  
// compile with: /EHsc  
#include <iostream>  
  
template<typename T>  
class X : public T {  
public:  
   void Dump() {  
      std::cout << "In X<T>::Dump()" << std::endl;  
  
      __if_exists(T::Dump) {  
         T::Dump();  
      }  
  
      __if_not_exists(T::Dump) {  
         std::cout << "T::Dump does not exist" << std::endl;  
      }  
   }     
};  
  
class A {  
public:  
   void Dump() {  
      std::cout << "In A::Dump()" << std::endl;  
   }  
};  
  
class B {};  
  
bool g_bFlag = true;  
  
class C {  
public:  
   void f(int);  
   void f(double);  
};  
  
int main() {   
   X<A> x1;  
   X<B> x2;  
  
   x1.Dump();  
   x2.Dump();  
  
   __if_exists(::g_bFlag) {  
      std::cout << "g_bFlag = " << g_bFlag << std::endl;  
   }  
  
   __if_exists(C::f) {  
      std::cout << "C::f exists" << std::endl;  
   }  
  
   return 0;  
}  
```  
  
## <a name="output"></a>Resultado  
  
```  
In X<T>::Dump()  
In A::Dump()  
In X<T>::Dump()  
T::Dump does not exist  
g_bFlag = 1  
C::f exists  
```  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de selección](../cpp/selection-statements-cpp.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 [__if_not_exists (Instrucción)](../cpp/if-not-exists-statement.md)
