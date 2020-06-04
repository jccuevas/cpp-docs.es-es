---
title: '&lt;iostream&gt;'
ms.date: 09/20/2017
f1_keywords:
- <iostream>
- iostream/std::cerr
- iostream/std::cin
- iostream/std::clog
- iostream/std::cout
- iostream/std::wcerr
- iostream/std::wcin
- iostream/std::wclog
- iostream/std::wcout
helpviewer_keywords:
- iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
ms.openlocfilehash: 03afb777dc3926284cf0dc625e94a716ecdf5413
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375341"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Declara los objetos que controlan la lectura y escritura en los flujos estándar. Esta incluye a menudo el único encabezado que necesita para hacer la entrada y salida de un programa C++.

## <a name="syntax"></a>Sintaxis

```cpp
#include <iostream>
```

> [!NOTE]
> La \<biblioteca de> `#include <ios>` `#include <streambuf>`iostream utiliza las instrucciones , , `#include <istream>`, y `#include <ostream>` .

## <a name="remarks"></a>Observaciones

Los objetos se dividen en dos grupos:

- [Cin](#cin), [cout](#cout), [cerr](#cerr)y [clog](#clog) están orientados a bytes, realizando transferencias convencionales de byte a la vez.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr) y [wclog](#wclog) se orientan a caracteres anchos y traducen en ambas direcciones los caracteres anchos que el programa manipula internamente.

Una vez que se realizan determinadas operaciones en una secuencia, como la entrada estándar, no se pueden realizar operaciones de una orientación diferente en la misma secuencia. Por lo tanto, un programa no puede operar indistintamente en [cin](#cin) y [wcin,](#wcin)por ejemplo.

Todos los objetos declarados en este encabezado comparten una propiedad peculiar: puede suponer que \<se construyen antes que los objetos estáticos que defina, en una unidad de traducción que incluya> iostream. Del mismo modo, puede suponer que estos objetos no se destruyen antes que los destructores de los objetos estáticos que defina. (Sin embargo, las secuencias de salida se vacían durante la terminación del programa.) Por lo tanto, puede leer o escribir de forma segura en las secuencias estándar antes del inicio del programa y después de la finalización del programa.

Sin embargo, esta garantía no es universal. Un constructor estático puede llamar a una función en otra unidad de traducción. La función llamada no puede suponer que se han construido los objetos declarados en este encabezado, dado el orden incierto en el que las unidades de traducción participan en la construcción estática. Para usar esos objetos en este contexto, primero debe construir un objeto de clase [ios_base::Init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Objetos de flujo global

|||
|-|-|
|[cerr](#cerr)|Especifica el flujo global `cerr`.|
|[Cin](#cin)|Especifica el flujo global `cin`.|
|[Obstruir](#clog)|Especifica el flujo global `clog`.|
|[cout](#cout)|Especifica el flujo global `cout`.|
|[wcerr](#wcerr)|Especifica el flujo global `wcerr`.|
|[wcin](#wcin)|Especifica el flujo global `wcin`.|
|[wclog](#wclog)|Especifica el flujo global `wclog`.|
|[wcout](#wcout)|Especifica el flujo global `wcout`.|

### <a name="cerr"></a><a name="cerr"></a>cerr

El objeto `cerr` controla la salida a un búfer de flujo asociado al objeto `stderr`, declarado en \<cstdio>.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [ostream](../standard-library/ostream-typedefs.md#ostream).

#### <a name="remarks"></a>Observaciones

El objeto controla las inserciones no almacenadas en búfer en la salida de error estándar como un flujo de bytes. Una vez que se construye el objeto, la expresión `cerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) es distinta de cero, y `cerr.tie() == &cout`.

#### <a name="example"></a>Ejemplo

```cpp
// iostream_cerr.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void TestWide( )
{
   int i = 0;
   wcout << L"Enter a number: ";
   wcin >> i;
   wcerr << L"test for wcerr" << endl;
   wclog << L"test for wclog" << endl;
}

int main( )
{
   int i = 0;
   cout << "Enter a number: ";
   cin >> i;
   cerr << "test for cerr" << endl;
   clog << "test for clog" << endl;
   TestWide( );
}
```

### <a name="cin"></a><a name="cin"></a>Cin

Especifica el flujo global `cin`.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [istream](../standard-library/istream-typedefs.md#istream).

#### <a name="remarks"></a>Observaciones

El objeto controla las extracciones de la entrada estándar como un flujo de bytes. Una vez que se construye el objeto, la llamada `cin.`[tie](../standard-library/basic-ios-class.md#tie) devuelve `&`[cout](#cout).

#### <a name="example"></a>Ejemplo

En este `cin` ejemplo, establece el bit de error en la secuencia cuando se encuentra con caracteres no numéricos. El programa borra el bit de error y elimina el carácter no válido de la secuencia para continuar.

```cpp
// iostream_cin.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
   int x;
   cout << "enter choice:";
   cin >> x;
   while (x < 1 || x > 4)
   {
      cout << "Invalid choice, try again:";
      cin >> x;
      // not a numeric character, probably
      // clear the failure and pull off the non-numeric character
      if (cin.fail())
      {
         cin.clear();
         char c;
         cin >> c;
      }
   }
}
```

```Output
2
```

### <a name="clog"></a><a name="clog"></a>Obstruir

Especifica el flujo global `clog`.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [ostream](../standard-library/ostream-typedefs.md#ostream).

#### <a name="remarks"></a>Observaciones

El objeto controla las inserciones almacenadas en búfer en la salida de error estándar como un flujo de bytes.

#### <a name="example"></a>Ejemplo

Vea [cerr](#cerr) para obtener un ejemplo que usa `clog`.

### <a name="cout"></a><a name="cout"></a>cout

Especifica el flujo global `cout`.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [ostream](../standard-library/ostream-typedefs.md#ostream).

#### <a name="remarks"></a>Observaciones

El objeto controla las inserciones en la salida estándar como un flujo de bytes.

#### <a name="example"></a>Ejemplo

Vea [cerr](#cerr) para obtener un ejemplo que usa `cout`.

### <a name="wcerr"></a><a name="wcerr"></a>wcerr

Especifica el flujo global `wcerr`.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [wostream](../standard-library/ostream-typedefs.md#wostream).

#### <a name="remarks"></a>Observaciones

El objeto controla las inserciones no almacenadas en búfer en la salida de error estándar como un flujo amplio. Una vez que se construye el objeto, la expresión `wcerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) es distinta de cero.

#### <a name="example"></a>Ejemplo

Vea [cerr](#cerr) para obtener un ejemplo que usa `wcerr`.

### <a name="wcin"></a><a name="wcin"></a>wcin

Especifica el flujo global `wcin`.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [wistream](../standard-library/istream-typedefs.md#wistream).

#### <a name="remarks"></a>Observaciones

El objeto controla las extracciones de la entrada estándar como un flujo ancho. Una vez que se construye el objeto, la llamada `wcin.`[tie](../standard-library/basic-ios-class.md#tie) devuelve `&`[wcout](#wcout).

#### <a name="example"></a>Ejemplo

Vea [cerr](#cerr) para obtener un ejemplo que usa `wcin`.

### <a name="wclog"></a><a name="wclog"></a>wclog

Especifica el flujo global `wclog`.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [wostream](../standard-library/ostream-typedefs.md#wostream).

#### <a name="remarks"></a>Observaciones

El objeto controla las inserciones almacenadas en búfer en la salida de error estándar como un flujo ancho.

#### <a name="example"></a>Ejemplo

Vea [cerr](#cerr) para obtener un ejemplo que usa `wclog`.

### <a name="wcout"></a><a name="wcout"></a>wcout

Especifica el flujo global `wcout`.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [wostream](../standard-library/ostream-typedefs.md#wostream).

#### <a name="remarks"></a>Observaciones

El objeto controla las inserciones en la salida estándar como secuencia amplia.

#### <a name="example"></a>Ejemplo

Vea [cerr](#cerr) para obtener un ejemplo que usa `wcout`.

Las instancias `CString` de una instrucción `wcout` deben convertirse a `const wchar_t*`, como se muestra en el siguiente ejemplo.

```cpp
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

Para obtener más información, vea [Operaciones básicas de CString](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
