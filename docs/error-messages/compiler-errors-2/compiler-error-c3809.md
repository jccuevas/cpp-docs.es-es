---
title: Error del compilador C3809
ms.date: 11/04/2016
f1_keywords:
- C3809
helpviewer_keywords:
- C3809
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
ms.openlocfilehash: 5ff57050980ddb770ea2fcfa4d0be4f42f5ee834
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391899"
---
# <a name="compiler-error-c3809"></a>Error del compilador C3809

'class': un tipo administrado o WinRT no puede tener ninguna función, clase o interfaz friend

Los tipos administrados y los tipos de Windows Runtime no permiten elementos friend. Para corregir este error, no declare elementos friend dentro administrados o tipos de Windows en tiempo de ejecución.

El siguiente ejemplo genera el error C3809:

```
// C3809a.cpp
// compile with: /clr
ref class A {};

ref class B
{
public:
   friend ref class A;   // C3809
};

int main()
{
}
```