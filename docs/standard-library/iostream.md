---
title: '&lt;iostream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 09/20/2017
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed484dcfdb94b60545a84563c77a3f242cc6c316
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Declara los objetos que controlan la lectura y escritura en los flujos estándar. Suele ser el único encabezado que es necesario incluir para realizar la entrada y salida de un programa de C++.

## <a name="syntax"></a>Sintaxis

```cpp
#include <iostream>

```

## <a name="remarks"></a>Comentarios

Los objetos se dividen en dos grupos:

- [cin](#cin), [cout](#cout), [cerr](#cerr) y [clog](#clog) están orientados a bytes y realizan transferencias convencionales byte por byte.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr) y [wclog](#wclog) se orientan a caracteres anchos y traducen en ambas direcciones los caracteres anchos que el programa manipula internamente.

Tras realizar determinadas operaciones en un flujo, como la entrada estándar, no es posible realizar operaciones de orientación en ese mismo flujo. Por lo tanto, un programa no puede funcionar indistintamente tanto con [cin](#cin) como con [wcin](#wcin), por ejemplo.

Todos los objetos que se declaran en este encabezado tienen en común una propiedad peculiar: se puede suponer que se construyen antes que cualquier objeto estático que se defina, en una unidad de traducción que incluye \<iostream>. De igual forma, se puede suponer que estos objetos no se destruyen antes que los destructores de todos esos objetos estáticos que se definen. (Sin embargo, los flujos de salida se vacían durante la finalización del programa). Por lo tanto, puede leer o escribir sin ningún riesgo en los flujos estándar antes de iniciar el programa y después de la finalización del programa.

Pero esta garantía no es universal. Un constructor estático puede llamar a una función en otra unidad de traducción. La función a la que se llama no puede suponer que se han construido los objetos que se declaran en el encabezado, dada la incertidumbre del orden con el que las unidades de traducción participan en la construcción estática. Para usar esos objetos en este contexto, primero debe construir un objeto de clase [ios_base::Init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Objetos de flujo global

|||
|-|-|
|[cerr](#cerr)|Especifica el flujo global `cerr`.|
|[cin](#cin)|Especifica el flujo global `cin`.|
|[clog](#clog)|Especifica el flujo global `clog`.|
|[cout](#cout)|Especifica el flujo global `cout`.|
|[wcerr](#wcerr)|Especifica el flujo global `wcerr`.|
|[wcin](#wcin)|Especifica el flujo global `wcin`.|
|[wclog](#wclog)|Especifica el flujo global `wclog`.|
|[wcout](#wcout)|Especifica el flujo global `wcout`.|

###  <a name="cerr"></a>  cerr

El objeto `cerr` controla la salida a un búfer de flujo asociado al objeto `stderr`, declarado en \<cstdio>.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [ostream](../standard-library/ostream-typedefs.md#ostream).

#### <a name="remarks"></a>Comentarios

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

###  <a name="cin"></a>  cin

Especifica el flujo global `cin`.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [istream](../standard-library/istream-typedefs.md#istream).

#### <a name="remarks"></a>Comentarios

El objeto controla las extracciones de la entrada estándar como un flujo de bytes. Una vez que se construye el objeto, la llamada `cin.`[tie](../standard-library/basic-ios-class.md#tie) devuelve `&`[cout](#cout).

#### <a name="example"></a>Ejemplo

En este ejemplo, `cin` establece el bit de error en el flujo cuando encuentra caracteres no numéricos. El sistema borra el bit de error y quita el carácter no válido del flujo para continuar.

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

###  <a name="clog"></a>  clog

Especifica el flujo global `clog`.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [ostream](../standard-library/ostream-typedefs.md#ostream).

#### <a name="remarks"></a>Comentarios

El objeto controla las inserciones almacenadas en búfer en la salida de error estándar como un flujo de bytes.

#### <a name="example"></a>Ejemplo

Vea [cerr](#cerr) para obtener un ejemplo que usa `clog`.

###  <a name="cout"></a>  cout

Especifica el flujo global `cout`.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [ostream](../standard-library/ostream-typedefs.md#ostream).

#### <a name="remarks"></a>Comentarios

El objeto controla las inserciones en la salida estándar como un flujo de bytes.

#### <a name="example"></a>Ejemplo

Vea [cerr](#cerr) para obtener un ejemplo que usa `cout`.

###  <a name="wcerr"></a>  wcerr

Especifica el flujo global `wcerr`.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [wostream](../standard-library/ostream-typedefs.md#wostream).

#### <a name="remarks"></a>Comentarios

El objeto controla las inserciones no almacenadas en búfer en la salida de error estándar como un flujo amplio. Una vez que se construye el objeto, la expresión `wcerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) es distinta de cero.

#### <a name="example"></a>Ejemplo

Vea [cerr](#cerr) para obtener un ejemplo que usa `wcerr`.

###  <a name="wcin"></a>  wcin

Especifica el flujo global `wcin`.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [wistream](../standard-library/istream-typedefs.md#wistream).

#### <a name="remarks"></a>Comentarios

El objeto controla las extracciones de la entrada estándar como un flujo ancho. Una vez que se construye el objeto, la llamada `wcin.`[tie](../standard-library/basic-ios-class.md#tie) devuelve `&`[wcout](#wcout).

#### <a name="example"></a>Ejemplo

Vea [cerr](#cerr) para obtener un ejemplo que usa `wcin`.

###  <a name="wclog"></a>  wclog

Especifica el flujo global `wclog`.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [wostream](../standard-library/ostream-typedefs.md#wostream).

#### <a name="remarks"></a>Comentarios

El objeto controla las inserciones almacenadas en búfer en la salida de error estándar como un flujo ancho.

#### <a name="example"></a>Ejemplo

Vea [cerr](#cerr) para obtener un ejemplo que usa `wclog`.

###  <a name="wcout"></a>  wcout

Especifica el flujo global `wcout`.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Valor devuelto

Objeto [wostream](../standard-library/ostream-typedefs.md#wostream).

#### <a name="remarks"></a>Comentarios

El objeto controla las inserciones en la salida estándar como secuencia amplia.

#### <a name="example"></a>Ejemplo

Vea [cerr](#cerr) para obtener un ejemplo que usa `wcout`.

Las instancias `CString` de una instrucción `wcout` deben convertirse a `const wchar_t*`, como se muestra en el siguiente ejemplo.

```

    CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;
```

Para obtener más información, vea [Operaciones básicas de CString](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
