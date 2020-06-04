---
title: __fastcall
ms.date: 12/17/2018
f1_keywords:
- __fastcall_cpp
- __fastcall
- _fastcall
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
ms.openlocfilehash: d4b650542a3a85c8f0008374abef02686c5491a3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188927"
---
# <a name="__fastcall"></a>__fastcall

**Específicos de Microsoft**

La Convención de llamada **__fastcall** especifica que los argumentos de las funciones se van a pasar en registros, siempre que sea posible. Esta convención de llamada solo se aplica a la arquitectura x86. En la lista siguiente se muestra la implementación de esta convención de llamada.

|Elemento|Implementación|
|-------------|--------------------|
|Orden de paso de argumento|Los primeros dos argumentos DWORD o menores que se encuentran en la lista de argumentos de izquierda a derecha se pasan en registros ECX y EDX; el resto de los argumentos se pasan en la pila de derecha a izquierda.|
|Responsabilidad de mantenimiento de pila|Al llamar a la función aparece el argumento de la pila.|
|Convención de creación de nombres representativos|El signo de arroba (\@) tiene como prefijo los nombres; un signo de arroba seguido del número de bytes (en formato decimal) en la lista de parámetros tiene como sufijo los nombres.|
|Convención de traducción de mayúsculas y minúsculas|No se lleva a cabo una traducción de mayúsculas y minúsculas.|

> [!NOTE]
> Las futuras versiones del compilador pueden utilizar distintos registros para almacenar parámetros.

El uso de la opción del compilador [/gr](../build/reference/gd-gr-gv-gz-calling-convention.md) hace que cada función del módulo se compile como **__fastcall** a menos que la función se declare mediante un atributo conflictivo o se `main`el nombre de la función.

Los compiladores que tienen como destino las arquitecturas ARM y x64 aceptan y omiten la palabra clave **__fastcall** . en un chip x64, por Convención, los primeros cuatro argumentos se pasan en registros cuando es posible y los argumentos adicionales se pasan en la pila. Para obtener más información, consulte la [Convención de llamada x64](../build/x64-calling-convention.md). En un chip ARM, se puede pasar hasta cuatro argumentos enteros y ocho argumentos de punto flotante en los registros; los argumentos adicionales se pasan en la pila.

En el caso de funciones de clase no estáticas, si la función se define fuera de línea, no es necesario especificar el modificador de convención de llamada en la definición fuera de línea. Es decir, para los métodos miembro no estáticos de clase, en el momento de la definición se supone la convención de llamada especificada durante la declaración. Dada esta definición de clase:

```cpp
struct CMyClass {
   void __fastcall mymethod();
};
```

esto:

```cpp
void CMyClass::mymethod() { return; }
```

equivale a esto:

```cpp
void __fastcall CMyClass::mymethod() { return; }
```

Por compatibilidad con versiones anteriores, **_fastcall** es un sinónimo de **__fastcall** a menos que se especifique la opción del compilador [/za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Ejemplo

En el siguiente ejemplo, se pasan argumentos a la función `DeleteAggrWrapper` en los registros:

```cpp
// Example of the __fastcall keyword
#define FASTCALL    __fastcall

void FASTCALL DeleteAggrWrapper(void* pWrapper);
// Example of the __ fastcall keyword on function pointer
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
