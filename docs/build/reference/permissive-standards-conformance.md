---
title: /permissive/ (Conformidad de los estándares)
description: Guía de referencia para la opción del compilador Microsoft C++ /permissive- (conformidad de estándares).
ms.date: 04/14/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 695f84e64f07128ac7744dc99e736f2a71ab3e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337399"
---
# <a name="permissive--standards-conformance"></a>/permissive/ (Conformidad de los estándares)

Especifique el modo de conformidad de estándares para el compilador. Utilice esta opción para ayudarle a identificar y solucionar problemas de conformidad en el código, para que sea más correcto y más portátil.

## <a name="syntax"></a>Sintaxis

> **/permisivo-**

## <a name="remarks"></a>Observaciones

Esta opción se admite en Visual Studio 2017 y versiones posteriores.

Puede usar la opción del compilador **/permissive-** para especificar el comportamiento del compilador conforme a los estándares. Esta opción deshabilita los comportamientos permisivos y establece las opciones del compilador [/Zc](zc-conformance.md) para la conformidad estricta. En el IDE, esta opción también hace que el motor de IntelliSense subraye el código no conforme.

De forma predeterminada, la opción **/permissive-** se establece en nuevos proyectos creados por Visual Studio 2017 versión 15.5 y versiones posteriores. No se establece de forma predeterminada en versiones anteriores. Cuando se establece la opción, el compilador genera errores de diagnóstico o advertencias cuando se detectan construcciones de lenguaje no estándar en el código, incluidos algunos errores comunes en el código anterior a C++11.

La opción **/permissive-** es compatible con casi todos los archivos de encabezado de los kits de Windows más recientes, como el Kit de desarrollo de software (SDK) o el Kit de controladores de Windows (WDK), a partir del SDK de Windows Fall Creators (10.0.16299.0). Es posible que las versiones anteriores del SDK no se compilen en **/permissive-** por diversos motivos de conformidad con el código fuente. El compilador y los SDKse se envían en diferentes escalas de tiempo de lanzamiento, por lo tanto, hay algunos problemas restantes. Para problemas específicos del archivo de encabezado, consulte Problemas de encabezado de [Windows](#windows-header-issues) a continuación.

La opción **/permissive-** establece las opciones [/Zc:referenceBinding](zc-referencebinding-enforce-reference-binding-rules.md), [/Zc:strictStrings](zc-strictstrings-disable-string-literal-type-conversion.md)y [/Zc:rvalueCast](zc-rvaluecast-enforce-type-conversion-rules.md) en comportamiento conforme. El valor predeterminado de estas opciones es un comportamiento no conforme. Puede pasar opciones **específicas de /Zc** después de **/permissive-** en la línea de comandos para invalidar este comportamiento.

En las versiones del compilador que comienzan en Visual Studio 2017 versión 15.3, la opción **/permissive-** establece la opción [/Zc:ternary.](zc-ternary.md) El compilador también implementa más de los requisitos para la búsqueda de nombres en dos fases. Cuando se establece la opción **/permissive-,** el compilador analiza las definiciones de plantilla de clase y función e identifica los nombres dependientes y no dependientes utilizados en las plantillas. En esta versión, solo se realiza el análisis de dependencia de nombres.

Las extensiones específicas del entorno y las áreas de lenguaje que el estándar deja hasta la implementación no se ven afectadas por **/permissive-**. Por ejemplo, el `__declspec`compilador no marca las directivas o atributos pragma específicos de Microsoft, convención de llamada y control de excepciones estructurados, y directivas o atributos pragma específicos del compilador en modo **/permissive-.**

La opción **/permissive-** utiliza la compatibilidad de conformidad en la versión actual del compilador para determinar qué construcciones de lenguaje no son conformes. La opción no determina si el código se ajusta a una versión específica del estándar C++. Para habilitar toda la compatibilidad del compilador implementada para el último borrador estándar, utilice la opción [/std:latest.](std-specify-language-standard-version.md) Para restringir la compatibilidad del compilador al estándar C++17 implementado actualmente, use la opción [/std:c++17.](std-specify-language-standard-version.md) Para restringir la compatibilidad del compilador para que coincida más estrechamente con el estándar C++14, utilice la opción [/std:c++14,](std-specify-language-standard-version.md) que es el valor predeterminado.

El compilador MSVC no admite todo el código compatible con estándares C++11, C++14 o C++17 en todas las versiones de Visual Studio 2017. Dependiendo de la versión de Visual Studio, la opción **/permissive-** puede no detectar problemas relacionados con algunos aspectos de la búsqueda de nombres en dos fases, enlazar una referencia no const a un temporal, tratar copy init como init directo, permitir varias conversiones definidas por el usuario en la inicialización, o tokens alternativos para operadores lógicos y otras áreas de conformidad no compatibles. Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md). Para aprovechar al máximo **/permissive-**, actualice Visual Studio a la versión más reciente.

### <a name="how-to-fix-your-code"></a>Cómo corregir el código

Estos son algunos ejemplos de código que se detecta como no conforme cuando se utiliza **/permissive-**, junto con formas sugeridas para solucionar los problemas.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Usar el valor predeterminado como identificador en el código nativo

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>Buscar miembros en la base dependiente

```cpp
template <typename T>
struct B {
    void f();
};

template <typename T>
struct D : public B<T> // B is a dependent base because its type
                       // depends on the type of T.
{
    // One possible fix is to uncomment the following line.
    // If this is a type, don't forget the 'typename' keyword.
    // using B<T>::f;

    void g() {
        f(); // error C3861: 'f': identifier not found
             // Another fix is to change it to 'this->f();'
    }
};

void h() {
    D<int> d;
    d.g();
}
```

#### <a name="use-of-qualified-names-in-member-declarations"></a>Uso de nombres calificados en declaraciones de miembros

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Inicializar varios miembros del sindicato en un inicializador de miembro

```cpp
union U
{
    U()
        : i(1), j(1) // error C3442: Initializing multiple members of
                     // union: 'U::i' and 'U::j'.
                     // Remove all but one of the initializations to fix.
    {}
    int i;
    int j;
};
```

#### <a name="hidden-friend-name-lookup-rules"></a>Reglas de búsqueda de nombres de amigos ocultos

```cpp
// Example 1
struct S {
    friend void f(S *);
};
// Uncomment this declaration to make the hidden friend visible:
// void f(S *); // This declaration makes the hidden friend visible

using type = void (*)(S *);
type p = &f; // error C2065: 'f': undeclared identifier.
```

```cpp
// Example 2
struct S {
    friend void f(S *);
};
void g() {
    // Using nullptr instead of S prevents argument dependent lookup in S
    f(nullptr); // error C3861: 'f': identifier not found

    S *p = nullptr;
    f(p); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>Usar enumeraciones con ámbito en límites de matriz

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Usar para cada uno en código nativo

```cpp
void func() {
    int array[] = {1, 2, 30, 40};
    for each (int i in array) // error C4496: nonstandard extension
                              // 'for each' used: replace with
                              // ranged-for statement:
                              // for (int i: array)
    {
        // ...
    }
}
```

#### <a name="use-of-atl-attributes"></a>Uso de atributos ATL

```cpp
// Example 1
[uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
class A {};
```

```cpp
// Fix for example 1
class __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) B {};
```

```cpp
// Example 2
[emitidl];
[module(name="Foo")];

[object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
__interface ICustom {
    HRESULT Custom([in] longl, [out, retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out, retval] long*pLong);
};

[coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
class CFoo : public ICustom
{};
```

```cpp
// Fix for example 2
// First, create the *.idl file. The vc140.idl generated file can be
// used to automatically obtain a *.idl file for the interfaces with
// annotation. Second, add a midl step to your build system to make
// sure that the C++ interface definitions are outputted.
// Last, adjust your existing code to use ATL directly as shown in
// the atl implementation section.

-- IDL  FILE--
import "docobj.idl";

[object, local, uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)]
interface ICustom : IUnknown {
    HRESULT Custom([in] longl, [out,retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out,retval] long*pLong);
};

[ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
library Foo {
    importlib("stdole2.tlb");
    importlib("olepro32.dll");

    [version(1.0), appobject, uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)]
    coclass CFoo { interface ICustom; };
}

-- ATL IMPLEMENTATION--
#include <idl.header.h>
#include <atlbase.h>

class ATL_NO_VTABLE CFooImpl : public ICustom,
    public ATL::CComObjectRootEx<CComMultiThreadModel>
{
    public:BEGIN_COM_MAP(CFooImpl)
    COM_INTERFACE_ENTRY(ICustom)
    END_COM_MAP()
};
```

#### <a name="ambiguous-conditional-operator-arguments"></a>Argumentos de operador condicional ambiguo

En versiones del compilador anteriores a Visual Studio 2017 versión 15.3, el `?:` compilador aceptó argumentos para el operador condicional (o operador ternario) que el Standard considera ambiguo. En el modo **/permissive-,** el compilador emite ahora uno o varios diagnósticos en casos que se compilaron sin diagnósticos en versiones anteriores.

Los errores comunes que pueden resultar de este cambio incluyen:

- error C2593: 'operador ?' es ambiguo

- error C2679: binario '?': no se ha encontrado ningún operador que tome un operando derecho de tipo 'B' (o no haya una conversión aceptable)

- error C2678: binario '?': no se ha encontrado ningún operador que tome un operando izquierdo de tipo 'A' (o no haya una conversión aceptable)

- error C2446: ':': no hay conversión de 'B' a 'A'

Un patrón de código típico que puede causar este problema es cuando alguna clase C proporciona un constructor no explícito de otro tipo T y un operador de conversión no explícito al tipo T. En este caso, tanto la conversión del segundo argumento al tipo del tercer argumento como la conversión del tercer argumento al tipo del segundo argumento son conversiones válidas. Dado que ambos son válidos, es ambiguo de acuerdo con el estándar.

```cpp
// Example 1: class that provides conversion to and initialization from some type T
struct A
{
    A(int);
    operator int() const;
};

extern bool cond;

A a(42);
// Accepted when /Zc:ternary or /permissive- is not used:
auto x = cond ? 7 : a; // A: permissive behavior prefers A(7) over (int)a
// Accepted always:
auto y = cond ? 7 : int(a);
auto z = cond ? A(7) : a;
```

Hay una excepción importante a este patrón común cuando T representa uno de `const char *` `const char16_t *`los tipos de cadena terminados `?:` en null (por ejemplo, , , etc.) y el argumento real a es un literal de cadena de tipo correspondiente. C++17 ha cambiado la semántica de C++14. Como resultado, el código del ejemplo 2 se acepta en **/std:c++14** y se rechaza en **/std:c++17** cuando se utiliza **/Zc:ternary** o **/permissive-.**

```cpp
// Example 2: exception from the above
struct MyString
{
    MyString(const char* s = "") noexcept;  // from char*
    operator const char* () const noexcept; //   to char*
};

extern bool cond;

MyString s;
// Using /std:c++14, /permissive- or /Zc:ternary behavior
// is to prefer MyString("A") over (const char*)s
// but under /std:c++17 this line causes error C2445:
auto x = cond ? "A" : s;
// You can use a static_cast to resolve the ambiguity:
auto y = cond ? "A" : static_cast<const char*>(s);
```

Otro caso en el que puede ver errores `void`es en operadores condicionales con un argumento de tipo . Este caso puede ser común en macros similares a ASSERT.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

También puede ver errores en la metaprogramación de plantillas, donde los tipos de resultados de operador condicional pueden cambiar en **/Zc:ternary** y **/permissive-**. Una forma de resolver este problema es usar [std::remove_reference](../../standard-library/remove-reference-class.md) en el tipo resultante.

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>Búsqueda de nombres en dos fases

Cuando se establece la opción **/permissive-,** el compilador analiza las definiciones de plantilla de clase y función, identificando los nombres dependientes y no dependientes utilizados en las plantillas según sea necesario para la búsqueda de nombres de dos fases. En Visual Studio 2017 versión 15.3, se realiza el análisis de dependencia de nombres. En particular, los nombres no dependientes que no se declaran en el contexto de una definición de plantilla provocan un mensaje de diagnóstico según lo requieran los estándares ISO C++. En Visual Studio 2017 versión 15.7, también se realiza el enlace de nombres no dependientes que requieren búsqueda dependiente de argumentos en el contexto de definición.

```cpp
// dependent base
struct B {
    void g() {}
};

template<typename T>
struct D : T {
    void f() {
        // The call to g was incorrectly allowed in VS2017:
        g();  // Now under /permissive-: C3861
        // Possible fixes:
        // this->g();
        // T::g();
    }
};

int main()
{
    D<B> d;
    d.f();
}
```

Si desea un comportamiento heredado para la búsqueda en dos fases, pero de lo contrario desea **/permissive-** comportamiento, agregue la opción **/Zc:twoPhase-.**

### <a name="windows-header-issues"></a>Problemas de encabezado de Windows

La opción **/permissive-** es demasiado estricta para las versiones de los Kits de Windows anteriores a Windows Fall Creators Update SDK (10.0.16299.0) o la versión 1709 del Kit de controladores de Windows (WDK). Le recomendamos que actualice a las últimas versiones de los Kits de Windows para poder utilizar **/permissive-** en el código del controlador de Windows o dispositivo.

Ciertos archivos de encabezado en el SDK de actualización de Windows de abril de 2018 (10.0.17134.0), el SDK de Windows Fall Creators Update (10.0.16299.0) o el Kit de controladores de Windows (WDK) 1709, todavía tienen problemas que los hacen incompatibles con el uso de **/permissive-**. Para evitar estos problemas, se recomienda restringir el uso de estos encabezados solo a los archivos de código fuente que los requieran y quitar la opción **/permissive-** al compilar esos archivos de código fuente específicos.

Estos encabezados WRL de WinRT publicados en el SDK de actualización de Windows de abril de 2018 (10.0.17134.0) no están limpios con **/permissive-**. Para evitar estos problemas, no utilice **/permissive-**, o utilice **/permissive-** con **/Zc:twoPhase-** cuando trabaje con estos encabezados:

- Problemas en winrt/wrl/async.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Problema en winrt/wrl/implements.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Estos encabezados de modo de usuario publicados en el SDK de actualización de Windows de abril de 2018 (10.0.17134.0) no están limpios con **/permissive-**. Para evitar estos problemas, no utilice **/permissive-** al trabajar con estos encabezados:

- Problemas en um/Tune.h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Problema en um/spddkhlp.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Problemas en um/refptrco.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Estos problemas son específicos de los encabezados del modo de usuario en el SDK de Windows Fall Creators Update (10.0.16299.0):

- Problema en um/Query.h

   Cuando se utiliza el modificador del compilador `tagRESTRICTION` **/permissive-,** la estructura no se compila debido al miembro case(RTOr) 'o'.

   ```cpp
   struct tagRESTRICTION
   {
       ULONG rt;
       ULONG weight;
       /* [switch_is][switch_type] */ union _URes
       {
           /* [case()] */ NODERESTRICTION ar;
           /* [case()] */ NODERESTRICTION or;  // error C2059: syntax error: '||'
           /* [case()] */ NODERESTRICTION pxr;
           /* [case()] */ VECTORRESTRICTION vr;
           /* [case()] */ NOTRESTRICTION nr;
           /* [case()] */ CONTENTRESTRICTION cr;
           /* [case()] */ NATLANGUAGERESTRICTION nlr;
           /* [case()] */ PROPERTYRESTRICTION pr;
           /* [default] */  /* Empty union arm */
       } res;
   };
   ```

   Para solucionar este problema, compile archivos que incluyan Query.h sin la opción **/permissive-.**

- Problema en um/cellularapi_oem.h

   Cuando se utiliza el modificador del compilador **/permissive-,** la declaración forward de `enum UICCDATASTOREACCESSMODE` provoca una advertencia:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   La declaración forward de unscoped enum es una extensión de Microsoft. Para solucionar este problema, compile archivos que incluyan cellularapi_oem.h sin la opción **/permissive-** o utilice la opción [/wd](compiler-option-warning-level.md) para silenciar la advertencia C4471.

- Problema en um/omscript.h

   En C++03, una conversión de un literal de cadena a BSTR (que es una def de tipo a 'wchar_t *') está en desuso, pero se permite. En C++11, la conversión ya no está permitida.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Para solucionar este problema, compile archivos que incluyan omscript.h sin la opción **/permissive-** o utilice **/Zc:strictStrings-** en su lugar.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

En Visual Studio 2017 versión 15.5 y versiones posteriores, use este procedimiento:

1. Abra el cuadro de diálogo **Páginas** de propiedades del proyecto.

1. Seleccione la página de propiedades **Propiedades** > de configuración**C/C++** > **Language.**

1. Cambie el valor de la propiedad Modo de **conformidad** a **Sí (/permisivo-).** Elija **Aceptar** o **Aplicar** para guardar los cambios.

En versiones anteriores a Visual Studio 2017 versión 15.5, use este procedimiento:

1. Abra el cuadro de diálogo **Páginas** de propiedades del proyecto.

1. Seleccione la página de**propiedades** **De propiedades** > de configuración**C/C++.** > 

1. Escriba la opción del compilador **/permissive-** en el cuadro **Opciones adicionales.** Elija **Aceptar** o **Aplicar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador MSVC](compiler-options.md)\
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
