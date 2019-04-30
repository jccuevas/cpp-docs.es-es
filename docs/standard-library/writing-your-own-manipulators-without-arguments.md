---
title: Escribir manipuladores propios sin argumentos
ms.date: 11/04/2016
helpviewer_keywords:
- manipulators
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
ms.openlocfilehash: 0c3037c007e9388485f9553f9d2b0a69a1980b9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410829"
---
# <a name="writing-your-own-manipulators-without-arguments"></a>Escribir manipuladores propios sin argumentos

Escribir manipuladores que no usan argumentos no requiere la derivación de clases ni el uso de macros complejas. Supongamos que su impresora requiere el par \<ESC >[ para entrar en modo de negrita. Puede insertar este par directamente en la secuencia:

```cpp
cout << "regular " << '\033' << '[' << "boldface" << endl;
```

O puede definir el manipulador `bold`, que inserta los caracteres:

```cpp
ostream& bold(ostream& os) {
    return os << '\033' << '[';
}
cout << "regular " << bold << "boldface" << endl;
```

La función `bold` definida globalmente toma un argumento de referencia `ostream` y devuelve la referencia `ostream`. No es una función miembro ni una función friend porque no necesita tener acceso a los elementos de ninguna clase privada. La función `bold` se conecta a la secuencia porque el operador `<<` de la secuencia se sobrecarga para aceptar este tipo de función, mediante una declaración de aspecto similar al siguiente:

```cpp
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))
{
    // call ios_base manipulator
    (*_Pfn)(*(ios_base *)this);

    return (*this);
}
```

Puede usar esta característica para ampliar otros operadores sobrecargados. En este caso, que `bold` inserte caracteres en la secuencia es algo eventual. La función se llama cuando se inserta en la secuencia, no necesariamente cuando se imprimen los caracteres adyacentes. Por tanto, la impresión podría retrasarse debido al almacenamiento en búfer de la secuencia.

## <a name="see-also"></a>Vea también

[Flujos de salida](../standard-library/output-streams.md)<br/>
