---
title: Error del compilador C3807
ms.date: 11/04/2016
f1_keywords:
- C3807
helpviewer_keywords:
- C3807
ms.assetid: 7e2b0aab-8c61-4e71-b9c1-fcaeb6a1b5ea
ms.openlocfilehash: b5599914666af95a29667acc1ad4ad35eef7608f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391938"
---
# <a name="compiler-error-c3807"></a>Error del compilador C3807

'type': una clase con el atributo ComImport no puede derivar de 'tipo2', se permite solo la implementación de interfaz

Un tipo que derive de <xref:System.Runtime.InteropServices.ComImportAttribute> sólo se puede implementar una interfaz.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3807.

```
// C3807.cpp
// compile with: /clr /c
ref struct S {};
interface struct I {};

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 : S {};   // C3807
ref struct S2 : I {};
```