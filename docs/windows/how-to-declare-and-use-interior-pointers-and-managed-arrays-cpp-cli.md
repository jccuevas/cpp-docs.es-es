---
title: 'Cómo: Declarar y usar punteros internos y matrices administradas (C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, interior
- arrays [C++], managed
ms.assetid: e61a2c09-a7d0-4867-91ea-6b8788a01079
ms.openlocfilehash: 98f198812654706792ea18024bb8654803d27970
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598268"
---
# <a name="how-to-declare-and-use-interior-pointers-and-managed-arrays-ccli"></a>Cómo: Declarar y usar punteros internos y matrices administradas (C++/CLI)

El siguiente C++ / c++ / CLI muestra cómo puede declarar y usar un puntero interior a una matriz.

> [!IMPORTANT]
> Esta característica del lenguaje es compatible con la `/clr` opción del compilador, pero no mediante el `/ZW` opción del compilador.

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```cpp
// interior_ptr_arrays.cpp
// compile with: /clr
#define SIZE 10

int main() {
   // declare the array
   array<int>^ arr = gcnew array<int>(SIZE);

   // initialize the array
   for (int i = 0 ; i < SIZE ; i++)
      arr[i] = i + 1;

   // create an interior pointer into the array
   interior_ptr<int> ipi = &arr[0];

   System::Console::WriteLine("1st element in arr holds: {0}", arr[0]);
   System::Console::WriteLine("ipi points to memory address whose value is: {0}", *ipi);

   ipi++;
   System::Console::WriteLine("after incrementing ipi, it points to memory address whose value is: {0}", *ipi);
}
```

```Output
1st element in arr holds: 1
ipi points to memory address whose value is: 1
after incrementing ipi, it points to memory address whose value is: 2
```

## <a name="see-also"></a>Vea también

[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)