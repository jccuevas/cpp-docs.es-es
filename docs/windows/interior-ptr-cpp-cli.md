---
title: interior_ptr (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a83182151ccb85b920a37713b70df53b383b8919
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879112"
---
# <a name="interiorptr-ccli"></a>interior_ptr (C++/CLI)
Un *puntero interior* declara un puntero a dentro de un tipo de referencia, pero no para el propio objeto. Un puntero interior puede apuntar a un identificador de referencia, tipo de valor, el identificador del tipo de conversión boxing, miembro de un tipo administrado, o a un elemento de una matriz administrada.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 (No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes).  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 (No hay notas para esta característica de lenguaje que solo se apliquen a Windows Runtime).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 En el ejemplo de sintaxis siguiente se muestra un puntero interior.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
cli::interior_ptr<cv_qualifier type> var = &initializer;  
```  
  
### <a name="parameters"></a>Parámetros  
 *cv_qualifier*  
 **Const** o `volatile` calificadores.  
  
 *type*  
 El tipo de *inicializador*.  
  
 *var*  
 El nombre de la `interior_ptr` variable.  
  
 *initializer*  
 Un miembro de un tipo de referencia, el elemento de una matriz administrada o cualquier otro objeto que se puede asignar a un puntero nativo.  
  
### <a name="remarks"></a>Comentarios  
 Un puntero nativo no es capaz de realizar el seguimiento de un elemento como cambios en su ubicación en el montón administrado, lo que resulta del recolector de elementos no utilizados mueve instancias de un objeto. Si hay un puntero hacer referencia correctamente a la instancia, el tiempo de ejecución debe actualizar el puntero al objeto recién posicionado.  
  
 Un `interior_ptr` representa un supraconjunto de la funcionalidad de un puntero nativo.  Por lo tanto, todo lo que puede asignarse a un puntero nativo también pueden asignarse a un `interior_ptr`.  Se permite un puntero interior a realizar el mismo conjunto de operaciones como punteros nativos, incluida la comparación y la aritmética con punteros.  
  
 Solo se puede declarar un puntero interior en la pila.  Un puntero interior no pueden declararse como un miembro de una clase.  
  
 Puesto que los punteros interiores existen solo en la pila, tomar la dirección de un puntero interior da como resultado un puntero no administrado.  
  
 `interior_ptr` tiene una conversión implícita a `bool`, lo que permite su uso en instrucciones condicionales.  
  
 Para obtener información sobre cómo declarar un puntero interior que apunta a un objeto que no se pueden mover en el montón de recolección, consulte [pin_ptr](../windows/pin-ptr-cpp-cli.md).  
  
 `interior_ptr` se encuentra en el espacio de nombres cli.  Vea [plataforma, predeterminado y cli espacios de nombres](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) para obtener más información.  
  
 Para obtener más información sobre los punteros interiores, vea  
  
-   [Procedimiento para declarar y usar punteros internos y matrices administradas (C++/CLI)](../windows/how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)  
  
-   [Procedimiento para declarar tipos de valor con la palabra clave interior_ptr (C++/CLI)](../windows/how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)  
  
-   [Procedimiento para sobrecargar funciones con punteros internos y punteros nativos (C++/CLI)](../windows/how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)  
  
-   [Procedimiento para declarar punteros internos con la palabra clave const (C++/CLI)](../windows/how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 El ejemplo siguiente muestra cómo declarar y utilizar un puntero interior en un tipo de referencia.  
  
```cpp  
// interior_ptr.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyClass {  
public:  
   int data;  
};  
  
int main() {  
   MyClass ^ h_MyClass = gcnew MyClass;  
   h_MyClass->data = 1;  
   Console::WriteLine(h_MyClass->data);  
  
   interior_ptr<int> p = &(h_MyClass->data);  
   *p = 2;  
   Console::WriteLine(h_MyClass->data);  
  
   // alternatively  
   interior_ptr<MyClass ^> p2 = &h_MyClass;  
   (*p2)->data = 3;  
   Console::WriteLine((*p2)->data);  
}  
```  
  
 **Salida**  
  
```Output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)