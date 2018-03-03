---
title: ref new, gcnew (extensiones de componentes de C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 616117f7274d6f68456aa23614fb354a71982fb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ref-new-gcnew--c-component-extensions"></a>ref new, gcnew (Extensiones de componentes de C++)
El `ref new` palabra clave agregada asigna una instancia de un tipo que se han recopilado cuando el objeto deja de estar accesible y que devuelve un identificador ([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)) al objeto asignado.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 La memoria para una instancia de un tipo que se asigna mediante `ref new` se desasigna automáticamente.  
  
 Una operación `ref new` inicia `OutOfMemoryException` si no puede asignar memoria.  
  
 Para obtener más información acerca de cómo se asignan y se desasigna memoria para tipos nativos de C++, vea [el nuevo y eliminar operadores](../cpp/new-and-delete-operators.md).  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 Use `ref new` para asignar memoria para objetos de Windows en tiempo de ejecución cuya duración desee administrar automáticamente. El objeto se desasigna automáticamente cuando su recuento de referencias llega a cero, lo que sucede después de que la última copia de la referencia salga del ámbito. Para obtener más información, consulte [clases y structs Ref](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 La memoria para un tipo administrado (tipo de valor o referencia) se asigna mediante `gcnew` y se desasigna mediante la colección de elementos no utilizados.  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 En el ejemplo siguiente se usa `gcnew` para asignar un objeto de mensaje.  
  
```  
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
  
 **Ejemplo**  
  
 En el ejemplo siguiente se usa `gcnew` para crear un tipo de valor con la conversión boxing aplicada para usarlo como tipo de referencia.  
  
```  
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
  
 **Salida**  
  
```Output  
32  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)