---
title: __raise
ms.date: 11/04/2016
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
ms.openlocfilehash: 9238e8e3e2fcd2c2f8b6431cfb0a79d452c5adf3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179177"
---
# <a name="__raise"></a>__raise

Resalta el sitio de llamada de un evento.

## <a name="syntax"></a>Sintaxis

```
__raise method-declarator;
```

## <a name="remarks"></a>Observaciones

En código administrado, un evento solo se puede generar desde dentro de la clase donde se define. Vea el [evento](../extensions/event-cpp-component-extensions.md) para obtener más información.

La palabra clave **__raise** provoca que se emita un error si se llama a un evento que no es de.

> [!NOTE]
>  Una clase o struct basada en plantilla no puede contener eventos.

## <a name="example"></a>Ejemplo

```cpp
// EventHandlingRef_raise.cpp
struct E {
   __event void func1();
   void func1(int) {}

   void func2() {}

   void b() {
      __raise func1();
      __raise func1(1);  // C3745: 'int Event::bar(int)':
                         // only an event can be 'raised'
      __raise func2();   // C3745
   }
};

int main() {
   E e;
   __raise e.func1();
   __raise e.func1(1);  // C3745
   __raise e.func2();   // C3745
}
```

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Control de eventos](../cpp/event-handling.md)<br/>
[Extensiones de componentes para plataformas de tiempo de ejecución](../extensions/component-extensions-for-runtime-platforms.md)
