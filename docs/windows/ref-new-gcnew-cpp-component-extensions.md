---
title: ref new, gcnew (extensiones de componente de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
dev_langs:
- C++
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed742d3762232846b2cac189978ea07c140b65f2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012662"
---
# <a name="ref-new-gcnew--c-component-extensions"></a>ref new, gcnew (Extensiones de componentes de C++)
El **referencia nuevos** palabra clave agregada asigna una instancia de un tipo que se recolecta cuando el objeto deja de estar accesible y que devuelve un identificador ([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)) al objeto asignado.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 Memoria para una instancia de un tipo que está asignada por **referencia nuevos** se desasigna automáticamente.  
  
 Un **referencia nuevos** operación produce `OutOfMemoryException` si no puede asignar memoria.  
  
 Para obtener más información acerca de cómo asigna y desasigna memoria para tipos nativos de C++, vea [el nuevo y eliminar operadores](../cpp/new-and-delete-operators.md).  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 Use **referencia nuevos** asignar memoria para objetos de Windows Runtime cuya duración desee administrar automáticamente. El objeto se desasigna automáticamente cuando su recuento de referencias llega a cero, lo que sucede después de que la última copia de la referencia salga del ámbito. Para obtener más información, consulte [clases y structs Ref](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: `/ZW`  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 Se asigna memoria para un tipo administrado (tipo de valor o referencia) por **gcnew**y se desasigna mediante la recolección de elementos.  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: `/clr`  
  
### <a name="examples"></a>Ejemplos  
  
 En el ejemplo siguiente se usa **gcnew** para asignar un objeto de mensaje.  
  
```cpp  
// mcppv2_gcnew_1.cpp  
// compile with: /clr  
ref struct Message {  
   System::String^ sender;  
   System::String^ receiver;  
   System::String^ data;  
};  
  
int main() {  
   Message^ h_Message  = gcnew Message;  
  //...  
}  
```  
  
 En el ejemplo siguiente se usa **gcnew** para crear un tipo de valor con conversión boxing para su uso como un tipo de referencia.  
  
```cpp  
// example2.cpp : main project file.  
// compile with /clr  
using namespace System;  
value class Boxed {  
    public:  
        int i;  
};  
int main()  
{  
    Boxed^ y = gcnew Boxed;  
    y->i = 32;  
    Console::WriteLine(y->i);  
    return 0;  
}  
```  
  
```Output  
32  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)