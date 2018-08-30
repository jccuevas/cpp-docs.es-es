---
title: Literales (C++) definido por el usuario | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76eac97c6d545f37ca13c640c80200e95a1938f9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208388"
---
# <a name="user-defined-literals--c"></a>Literales definidos por el usuario (C++)

Hay cinco categorías principales de literales: entero, carácter, punto flotante, cadena, booleano y puntero.  A partir de C++ 11, puede definir sus propios literales en función de estas categorías para proporcionar atajos sintácticos para expresiones comunes y aumentar la seguridad de tipos. Por ejemplo, supongamos que tiene una clase Distance. Puede definir un literal para kilómetros y otro para millas, y fomentar que usuario sea explícito sobre las unidades de medida escribiendo simplemente: auto d = 42,0_km o auto d = 42,0_mi. No hay ninguna ventaja ni desventaja de rendimiento con literales definidos por el usuario; se usan principalmente por comodidad o para la deducción de tipos de tiempo de compilación. La biblioteca estándar tiene literales definidos por el usuario para std: String, std:: Complex y unidades de tiempo y la duración de las operaciones en el \<chrono > encabezado:

```cpp
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)
    std::string str = "hello"s + "World"s;  // Standard Library <string> UDL
    complex<double> num =
        (2.0 + 3.01i) * (5.0 + 4.3i);       // Standard Library <complex> UDL
    auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs
```

## <a name="user-defined-literal-operator-signatures"></a>Firmas de operador literal definido por el usuario

Implementar un literal definido por el usuario mediante la definición de un **operador ""** en el ámbito de espacio de nombres con una de las formas siguientes:

```cpp
ReturnType operator "" _a(unsigned long long int);   // Literal operator for user-defined INTEGRAL literal
ReturnType operator "" _b(long double);              // Literal operator for user-defined FLOATING literal
ReturnType operator "" _c(char);                     // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _d(wchar_t);                  // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _e(char16_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _f(char32_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _g(const     char*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _h(const  wchar_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _i(const char16_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _g(const char32_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Los nombres de operador del ejemplo anterior son marcadores de posición para cualquier nombre que proporcione; sin embargo, el carácter de subrayado inicial es necesario. (Solo en la biblioteca estándar se permite definir literales sin el carácter de subrayado). En el tipo devuelto es donde se personaliza la conversión u otra operación que el literal realice. Además, cualquiera de estos operadores se puede definir como `constexpr`.

## <a name="cooked-literals"></a>Literales elaborados

En el código fuente cualquier literal, definido por el usuario o no, es esencialmente una secuencia de caracteres alfanuméricos, como `101`, `54.7`, `"hello"` o `true`. El compilador interpreta la secuencia como integer, float, const char\* cadena y así sucesivamente. Un valor literal definido por el usuario que acepta como entrada cualquier tipo que el compilador asignado al valor literal se conoce informalmente como un *literal cocido*. Todos los operadores anteriores, excepto `_r` y `_t`, son literales elaborados. Por ejemplo, un literal `42.0_km` se enlazaría a un operador denominado _km que tuviera una firma semejante a _b y el literal `42_km` se enlazaría a un operador con una firma semejante a _a.

En el ejemplo siguiente se muestra cómo los literales definidos por el usuario pueden fomentar que los llamadores sean explícitos sobre los datos proporcionados. Para crear un `Distance`, el usuario debe especificar explícitamente kilómetros o millas mediante el literal definido por el usuario adecuado. Por supuesto, también se puede lograr el mismo resultado de otras maneras, pero los literales definidos por el usuario son menos detallados que las alternativas.

```cpp
struct Distance
{
private:
    explicit Distance(long double val) : kilometers(val)
    {}

    friend Distance operator"" _km(long double  val);
    friend Distance operator"" _mi(long double val);
    long double kilometers{ 0 };
public:
    long double get_kilometers() { return kilometers; }
    Distance operator+(Distance& other)
    {
        return Distance(get_kilometers() + other.get_kilometers());
    }
};

Distance operator"" _km(long double  val)
{
    return Distance(val);
}

Distance operator"" _mi(long double val)
{
    return Distance(val * 1.6);
}
int main(int argc, char* argv[])
{
    // Must have a decimal point to bind to the operator we defined!
    Distance d{ 402.0_km }; // construct using kilometers
    cout << "Kilometers in d: " << d.get_kilometers() << endl; // 402

    Distance d2{ 402.0_mi }; // construct using miles
    cout << "Kilometers in d2: " << d2.get_kilometers() << endl;  //643.2

    // add distances constructed with different units
    Distance d3 = 36.0_mi + 42.0_km;
    cout << "d3 value = " << d3.get_kilometers() << endl; // 99.6

    // Distance d4(90.0); // error constructor not accessible

    string s;
    getline(cin, s);
    return 0;
}
```

Tenga en cuenta que el número literal debe usar un valor decimal, en caso contrario, el número se interpretaría como un número entero y el tipo no sería compatible con el operador. Tenga en cuenta también que para la entrada de punto flotante, el tipo debe ser **long double**y para los tipos enteros debe ser **long long**.

## <a name="raw-literals"></a>Literales sin formato

En un literal sin formato definido por el usuario, el operador que defina acepta el literal como una secuencia de valores char y deberá interpretar esa secuencia como un número, una cadena o un tipo diferente. En la lista de operadores mostrada anteriormente en esta página, se pueden usar `_r` y `_t` para definir literales sin formato:

```cpp
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Puede usar literales sin formato para proporcionar una interpretación personalizada de una secuencia de entrada que sea diferente de lo que realizaría el compilador. Por ejemplo, puede definir un literal que convierta la secuencia `4.75987` en un tipo Decimal personalizado en lugar de un tipo de punto flotante de IEEE 754. Los literales sin formato, como los literales elaborados, pueden usarse también para realizar la validación en tiempo de compilación de las secuencias de entrada.

### <a name="example-limitations-of-raw-literals"></a>Ejemplo: Limitaciones de literales sin formato

El operador literal sin formato y la plantilla de operador literal solo funcionan para literales de entero y de punto flotante definidos por el usuario, tal y como se muestra en el ejemplo siguiente:

```cpp
#include <cstddef>
#include <cstdio>

// Literal operator for user-defined INTEGRAL literal
void operator "" _dump(unsigned long long int lit)
{
    printf("operator \"\" _dump(unsigned long long int) : ===>%llu<===\n", lit);
};

// Literal operator for user-defined FLOATING literal
void operator "" _dump(long double lit)
{
    printf("operator \"\" _dump(long double)            : ===>%Lf<===\n",  lit);
};

// Literal operator for user-defined CHARACTER literal
void operator "" _dump(char lit)
{
    printf("operator \"\" _dump(char)                   : ===>%c<===\n",   lit);
};

void operator "" _dump(wchar_t lit)
{
    printf("operator \"\" _dump(wchar_t)                : ===>%d<===\n",   lit);
};

void operator "" _dump(char16_t lit)
{
    printf("operator \"\" _dump(char16_t)               : ===>%d<===\n",   lit);
};

void operator "" _dump(char32_t lit)
{
    printf("operator \"\" _dump(char32_t)               : ===>%d<===\n",   lit);
};

// Literal operator for user-defined STRING literal
void operator "" _dump(const     char* lit, size_t)
{
    printf("operator \"\" _dump(const     char*, size_t): ===>%s<===\n",   lit);
};

void operator "" _dump(const  wchar_t* lit, size_t)
{
    printf("operator \"\" _dump(const  wchar_t*, size_t): ===>%ls<===\n",  lit);
};

void operator "" _dump(const char16_t* lit, size_t)
{
    printf("operator \"\" _dump(const char16_t*, size_t):\n"                  );
};

void operator "" _dump(const char32_t* lit, size_t)
{
    printf("operator \"\" _dump(const char32_t*, size_t):\n"                  );
};

// Raw literal operator
void operator "" _dump_raw(const char* lit)
{
    printf("operator \"\" _dump_raw(const char*)        : ===>%s<===\n",   lit);
};

template<char...> void operator "" _dump_template();       // Literal operator template

int main(int argc, const char* argv[])
{
    42_dump;
    3.1415926_dump;
    3.14e+25_dump;
     'A'_dump;
    L'B'_dump;
    u'C'_dump;
    U'D'_dump;
      "Hello World"_dump;
     L"Wide String"_dump;
    u8"UTF-8 String"_dump;
     u"UTF-16 String"_dump;
     U"UTF-32 String"_dump;
    42_dump_raw;
    3.1415926_dump_raw;
    3.14e+25_dump_raw;

    // There is no raw literal operator or literal operator template support on these types:
    //  'A'_dump_raw;
    // L'B'_dump_raw;
    // u'C'_dump_raw;
    // U'D'_dump_raw;
    //   "Hello World"_dump_raw;
    //  L"Wide String"_dump_raw;
    // u8"UTF-8 String"_dump_raw;
    //  u"UTF-16 String"_dump_raw;
    //  U"UTF-32 String"_dump_raw;
}
```

```Output
operator "" _dump(unsigned long long int) : ===>42<===
operator "" _dump(long double)            : ===>3.141593<===
operator "" _dump(long double)            : ===>31399999999999998506827776.000000<===
operator "" _dump(char)                   : ===>A<===
operator "" _dump(wchar_t)                : ===>66<===
operator "" _dump(char16_t)               : ===>67<===
operator "" _dump(char32_t)               : ===>68<===
operator "" _dump(const     char*, size_t): ===>Hello World<===
operator "" _dump(const  wchar_t*, size_t): ===>Wide String<===
operator "" _dump(const     char*, size_t): ===>UTF-8 String<===
operator "" _dump(const char16_t*, size_t):
operator "" _dump(const char32_t*, size_t):
operator "" _dump_raw(const char*)        : ===>42<===
operator "" _dump_raw(const char*)        : ===>3.1415926<===
operator "" _dump_raw(const char*)        : ===>3.14e+25<===
```