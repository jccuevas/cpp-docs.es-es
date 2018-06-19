---
title: 'priority_queue:: priority_queue (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue::priority_queue
dev_langs:
- C++
helpviewer_keywords:
- priority_queue member [STL/CLR]
ms.assetid: aab423d7-959e-48fd-9028-e9f45f43cb8a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8cb50eed9dbfcbe9480a6588ff10f966f1888205
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163398"
---
# <a name="priorityqueuepriorityqueue-stlclr"></a>priority_queue::priority_queue (STL/CLR)
Construye un objeto de adaptador de contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
priority_queue();  
priority_queue(priority_queue<Value, Container> right);  
priority_queue(priority_queue<Value, Container> right);  
explicit priority_queue(value_compare^ pred);  
priority_queue(value_compare^ pred, container_type% cont);  
template<typename InIt>  
    priority_queue(InIt first, InIt last);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred, container_type% cont);  
```  
  
#### <a name="parameters"></a>Parámetros  
 cont.  
 Contenedor que se va a copiar.  
  
 first  
 Comienzo del intervalo que se va a insertar.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 pred  
 Orden de predicado de la secuencia controlada.  
  
 right  
 Objeto o intervalo que se va a insertar.  
  
## <a name="remarks"></a>Comentarios  
 El constructor:  
  
 `priority_queue();`  
  
 crea un contenedor vacío ajustado, con el predicado del orden predeterminado. Se usa para especificar una secuencia controlada inicial vacía, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `priority_queue(priority_queue<Value, Container>% right);`  
  
 crea un contenedor ajustado que es una copia de `right.get_container()`, con el predicado ordenación `right.value_comp()`. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de cola `right`, con el mismo predicado de ordenación.  
  
 El constructor:  
  
 `priority_queue(priority_queue<Value, Container>^ right);`  
  
 crea un contenedor ajustado que es una copia de `right->get_container()`, con el predicado ordenación `right->value_comp()`. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de cola `*right`, con el mismo predicado de ordenación.  
  
 El constructor:  
  
 `explicit priority_queue(value_compare^ pred);`  
  
 crea un contenedor vacío ajustado, con el predicado ordenación `pred`. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado.  
  
 El constructor:  
  
 `priority_queue(value_compare^ pred, container_type cont);`  
  
 crea un contenedor vacío ajustado, con el predicado ordenación `pred`, a continuación, inserta todos los elementos de `cont` se usa para especificar una secuencia controlada inicial de un contenedor existente, con el predicado de ordenación especificado.  
  
 El constructor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last);`  
  
 crea un contenedor vacío ajustado, con el predicado de ordenación predeterminado, a continuación, inserta la secuencia [`first`, `last`). Se usa para especificar una secuencia controlada inicial desde una eqeuence especificado, con el predicado de ordenación especificado.  
  
 El constructor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`  
  
 crea un contenedor vacío ajustado, con el predicado ordenación `pred`, a continuación, inserta la secuencia [`first`, `last`). Se usa para especificar una secuencia controlada inicial desde una seqeuence especificado, con el predicado de ordenación especificado.  
  
 El constructor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`  
  
 crea un contenedor vacío ajustado, con el predicado ordenación `pred`, a continuación, inserta todos los elementos de `cont` además de la secuencia [`first`, `last`). Se usa para especificar una secuencia controlada inicial de un contenedor existente y un seqeuence especificado, con el predicado de ordenación especificado.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_priority_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/deque>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
typedef cliext::deque<wchar_t> Mydeque;   
int main()   
    {   
// construct an empty container   
    Mypriority_queue c1;   
    Mypriority_queue::container_type^ wc1 = c1.get_container();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    for each (wchar_t elem in wc1)   
        c2.push(elem);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule by copying an underlying container   
    Mypriority_queue c2x =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
   for each (wchar_t elem in c2x.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mypriority_queue c3(wc1->begin(), wc1->end());   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mypriority_queue c4(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>());   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range, another container, and an ordering rule   
    Mypriority_queue c5(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c5.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mypriority_queue c6(c3);   
    for each (wchar_t elem in c6.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mypriority_queue c7(%c3);   
    for each (wchar_t elem in c7.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule, by copying an underlying container   
    Mypriority_queue c8 =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c8.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 c a b  
size() = 0  
 a c b  
 a c b  
 c a b  
 a c b  
 a a b c c b  
 c a b  
 c a b  
 a c b  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/cola >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::assign (STL/CLR)](../dotnet/priority-queue-assign-stl-clr.md)   
 [priority_queue::generic_container (STL/CLR)](../dotnet/priority-queue-generic-container-stl-clr.md)   
 [priority_queue::operator= (STL/CLR)](../dotnet/priority-queue-operator-assign-stl-clr.md)