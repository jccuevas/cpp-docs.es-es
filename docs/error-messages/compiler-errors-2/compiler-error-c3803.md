---
title: Error del compilador C3803
ms.date: 11/04/2016
f1_keywords:
- C3803
helpviewer_keywords:
- C3803
ms.assetid: bad5fb9a-ed9a-4c15-96e7-cf06e200a50d
ms.openlocfilehash: f6c255ec18d6dcf94f3ec022f09b173c2c66a1dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400102"
---
# <a name="compiler-error-c3803"></a>Error del compilador C3803

'property': propiedad tiene un tipo que no es compatible con uno de su descriptores de acceso 'descriptor de acceso'

El tipo de una propiedad definida con [propiedad](../../cpp/property-cpp.md) no coincide con el tipo de valor devuelto para una de sus funciones de descriptor de acceso.

El ejemplo siguiente genera C3803:

```
// C3803.cpp
struct A
{
   __declspec(property(get=GetIt)) int i;
   char GetIt()
   {
      return 0;
   }

   /*
   // try the following definition instead
   int GetIt()
   {
      return 0;
   }
   */
}; // C3803

int main()
{
}
```