---
title: / permissive-(conformidad con los estándares)
ms.date: 06/21/2018
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 5590996c7598016365bb122977084835830f95ab
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820798"
---
# <a name="permissive--standards-conformance"></a>/ permissive-(conformidad con los estándares)

Especifique el modo estándar de conformidad del compilador. Use esta opción para ayudarle a identificar y corregir problemas de conformidad en el código para que sea más correcto y más portátil.

## <a name="syntax"></a>Sintaxis

> **/permissive-**

## <a name="remarks"></a>Comentarios

Esta opción se admite en Visual Studio 2017 y versiones posteriores.

Puede usar el **/ permissive-** opción del compilador para especificar el comportamiento del compilador cumple las especificaciones de los estándares. Esta opción deshabilita permisivos comportamientos y establece el [/Zc](zc-conformance.md) opciones del compilador de cumplimiento estricto. En el IDE, esta opción también hace que el código de no cumple las especificaciones de subrayado de motor de IntelliSense.

De forma predeterminada, el **/ permissive-** opción está establecida en los nuevos proyectos creados mediante Visual Studio 2017 versión 15.5 y versiones posteriores. No se establece de forma predeterminada en versiones anteriores. Cuando la opción está establecida, el compilador genera errores de diagnóstico o advertencias al construcciones de lenguaje no estándar se detectan en el código, incluidos algunos errores comunes de pre-código C ++ 11.

El **/ permissive-** opción es compatible con casi todos los archivos de encabezado de los Kits de Windows más recientes, como el Kit de desarrollo de Software (SDK) o Windows Driver Kit (WDK), empezando en el SDK de Windows Fall Creators (10.0.16299.0). Puede que no se compilan en versiones anteriores del SDK de **/ permissive-** por diversas razones de compatibilidad de código de origen. El compilador y el SDK se incluyen en una versión diferente de escalas de tiempo, por lo tanto, hay algunos problemas restantes. Para problemas de archivos de encabezado específicos, consulte [problemas de encabezado de Windows](#windows-header-issues) a continuación.

El **/ permissive-** conjuntos de opciones la [/Zc: strictstrings](zc-conformance.md) y [/Zc: rvaluecast](zc-conformance.md) opciones al comportamiento de conformidad. El valor predeterminado para un comportamiento no conforme. Puede pasar específico **/Zc** opciones después **/ permissive-** en la línea de comandos para invalidar este comportamiento.

En las versiones del principio del compilador en Visual Studio 2017 versión 15.3, el **/ permissive-** conjuntos de opciones la [/Zc: ternary](zc-ternary.md) opción. El compilador también implementa más de los requisitos para la búsqueda de nombres en dos fases. Cuando el **/ permissive-** opción está activada, el compilador analiza definiciones de plantilla de función y de clase, identificación de nombres dependientes y no dependiente usado en las plantillas. En esta versión, se realiza solo análisis de dependencias de nombre.

Extensiones específicas del entorno y las áreas de idioma que el estándar deja hasta la implementación no se ven afectadas por **/ permissive-**. Por ejemplo, específico de Microsoft `__declspec`, convención de llamada y palabras clave y las directivas pragma del compilador específicas o atributos de control de excepciones estructurado no estén marcados por el compilador en **/ permissive-** modo.

El **/ permissive-** opción usa la compatibilidad con la versión actual del compilador para determinar qué construcciones de lenguaje son no conforme. La opción no determina si el código se ajusta a una versión concreta de C++ estándar. Para habilitar todo el soporte técnico para el estándar de borrador más reciente del compilador implementado, use el [/std:latest](std-specify-language-standard-version.md) opción. Para restringir la compatibilidad del compilador que está implementada actualmente C ++ 17 estándar, use el [/std: c ++ 17](std-specify-language-standard-version.md) opción. Para restringir la compatibilidad del compilador para hacerlos coincidir con el estándar C ++ 14, use el [/std: c ++ 14](std-specify-language-standard-version.md) opción, que es el valor predeterminado.

No todos los C ++ 11, C ++ 14 o C ++ 17 que cumple los estándares de código es compatible con el compilador de MSVC en Visual Studio 2017. Según la versión de Visual Studio, el **/ permissive-** opción no puede detectar problemas sobre algunos aspectos de la búsqueda de nombres en dos fases, enlazar una referencia distinta de const a un archivo temporal, tratando init copia como init directa, lo que permite varias conversiones definidas por el usuario en la inicialización o símbolos (token) alternativo para los operadores lógicos y otras áreas de conformidad que no son compatibles. Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md). Para obtener el máximo provecho de **/ permissive-**, actualización de Visual Studio a la versión más reciente.

### <a name="how-to-fix-your-code"></a>Cómo corregir el código

Estos son algunos ejemplos de código que se detecta como no conformes cuando se usa **/ permissive-**, además de las formas sugeridas para corregir los problemas.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Usar el valor predeterminado como un identificador en el código nativo

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="lookup-members-in-dependent-base"></a>Miembros de la búsqueda en base dependiente

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>Uso de nombres completos en las declaraciones de miembros

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Inicializar a varios miembros de unión en un inicializador de miembro

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

#### <a name="hidden-friend-name-lookup-rules"></a>Reglas de búsqueda del nombre oculto amigo

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
    f(S); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>Usar enumeraciones con ámbito en los límites de matriz

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Uso de cada una en código nativo

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

#### <a name="ambiguous-conditional-operator-arguments"></a>Argumentos del operador condicional ambigua

En las versiones del compilador antes de Visual Studio 2017 versión 15.3, el compilador acepta argumentos para el operador condicional (o el operador ternario) `?:` que se consideran ambiguos por el estándar. En **/ permissive-** modo, el compilador ahora emite uno o más diagnósticos en los casos que se compilan sin diagnósticos en versiones anteriores.

Common errores que pudieran derivarse de este cambio se incluyen:

- ¿Error C2593: 'operador'? es ambiguo

- Error C2679: binario '?': encontró ningún un operador que adopte un operando derecho de tipo 'B' (o no hay ninguna conversión aceptable)

- el error C2678: binario '?': encontró ningún operador que adopte un operando izquierdo de tipo "A" (o no hay ninguna conversión aceptable)

- Error C2446: ':': ninguna conversión de 'B' a 'A'

Un modelo de código típico que puede causar este problema es cuando alguna clase de C proporciona un constructor que no sea explícito de otro tipo T y un operador de conversión no explícita al tipo T. En este caso, la conversión de 2do argumento al tipo de los 3 y la conversión de 3er argumento al tipo del 2 º son conversiones válidas, que es ambiguo según el estándar.

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

Hay una excepción importante a este patrón común cuando T representa uno de los tipos de cadena terminada en null (por ejemplo, `const char *`, `const char16_t *`, etc.) y el argumento real `?:` es una cadena literal del tipo correspondiente. C ++ 17 ha cambiado la semántica de C ++ 14. Como resultado, se acepta el código de ejemplo 2 en **/std: c ++ 14** y rechazados en **/std: c ++ 17** cuando **/Zc: ternary** o **/permissive-** se utiliza.

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

Es otro caso donde puede ver los errores en los operadores condicionales con un argumento de tipo `void`. En este caso puede ser comunes en las macros de aserción similar.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

También puede ver los errores de plantilla de metaprogramación, donde pueden cambiar los tipos de resultado del operador condicional en **/Zc: ternary** y **/ permissive-**. Una manera de resolver este problema es usar [std::remove_reference](../../standard-library/remove-reference-class.md) en el tipo resultante.

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

Cuando el **/ permissive-** opción está activada, el compilador analiza definiciones de plantilla de función y de clase, que identifica el dependientes y no dependiente de los nombres utilizados en plantillas según sea necesario para la búsqueda de nombres en dos fases. En Visual Studio 2017 versión 15.3, se realizan el análisis de dependencias de nombre. En concreto, los nombres no dependientes que no se declaran en el contexto de una definición de plantilla provocar un mensaje de diagnóstico según sea necesario por los estándares ISO C++. En Visual Studio 2017 versión 15.7, también se realiza el enlace de nombres no dependientes que requieren argumentos dependientes de búsqueda en el contexto de la definición.

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

Si quiere comportamiento heredado para la búsqueda en dos fases, pero en caso contrario **/ permissive-** comportamiento, agregue el **/Zc:twoPhase-** opción.

### <a name="windows-header-issues"></a>Problemas de encabezado de Windows

El **/ permissive-** opción es demasiado estricta para las versiones de los Kits de Windows antes de SDK de Windows Fall Creators Update (10.0.16299.0) o la versión 1709 de Windows Driver Kit (WDK). Se recomienda actualizar a las versiones más recientes de los Kits de Windows para poder usar **/ permissive-** en el código de controlador de Windows o el dispositivo.

Algunos archivos de encabezado de Windows abril de 2018 Update SDK (10.0.17134.0), el SDK de Windows Fall Creators Update (10.0.16299.0) o Windows Driver Kit (WDK) 1709, todavía tienen problemas que hacerlos incompatibles con el uso de **/permissive-**. Para solucionar estos problemas, se recomienda restringir el uso de estos encabezados a solo los archivos de código fuente que necesiten y quitarán el **/ permissive-** opción al compilar esos archivos de código fuente específicas.

Estos encabezados de WinRT WRL publicados en el Windows de abril de 2018 Update SDK (10.0.17134.0) no son limpia con **/ permissive-**. Para solucionar estos problemas, no utilice **/ permissive-**, o bien usar **/ permissive-** con **/Zc:twoPhase-** cuando se trabaja con estos encabezados:

- Problemas de winrt/wrl/async.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Emitir en winrt/wrl/implements.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Estos encabezados de modo de usuario que publicó en el Windows de abril de 2018 Update SDK (10.0.17134.0) no son limpia con **/ permissive-**. Para solucionar estos problemas, no use **/ permissive-** cuando se trabaja con estos encabezados:

- Problemas de um/Tune.h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Issue in um/spddkhlp.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Problemas de um/refptrco.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Estos problemas son específicos a los encabezados de modo de usuario en el SDK de Windows Fall Creators Update (10.0.16299.0):

- Emitir en um/Query.h

   Cuando se usa el **/ permissive-** conmutador de compilador, el `tagRESTRICTION` estructura no se compila debido a los miembros de case(RTOr) 'o'.

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

   Para solucionar este problema, compile los archivos que incluyen Query.h sin el **/ permissive-** opción.

- Emitir en um/cellularapi_oem.h

   Cuando se usa el **/ permissive-** modificador del compilador, la declaración adelantada de `enum UICCDATASTOREACCESSMODE` genera una advertencia:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   La declaración adelantada de enumeración sin ámbito es una extensión de Microsoft. Para solucionar este problema, compile los archivos que incluyen cellularapi_oem.h sin el **/ permissive-** , o utilizar el [/wd](compiler-option-warning-level.md) opción para silenciar la advertencia C4471.

- Emitir en um/omscript.h

   En C ++ 03, una conversión de un literal de cadena a tipo BSTR (que es una definición de tipo para ' wchar_t *') está en desuso está permitida. En C ++ 11, ya no se permite la conversión.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Para solucionar este problema, compile los archivos que incluyen omscript.h sin el **/ permissive-** , o utilizar **/Zc:strictStrings-** en su lugar.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

En Visual Studio 2017 versión 15.5 y versiones posteriores, utilice este procedimiento:

1. Abra el proyecto **páginas de propiedades** cuadro de diálogo.

1. Seleccione el **propiedades de configuración** > **C o C++** > **lenguaje** página de propiedades.

1. Cambiar el **modo de conformidad** valor de propiedad **Sí (/ permissive-)**. Elija **Aceptar** o **aplicar** para guardar los cambios.

En las versiones anteriores de Visual Studio 2017 versión 15.5, use este procedimiento:

1. Abra el proyecto **páginas de propiedades** cuadro de diálogo.

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Escriba el **/ permissive-** opción del compilador en el **opciones adicionales** cuadro. Elija **Aceptar** o **aplicar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

- [Opciones del compilador MSVC](compiler-options.md)
- [Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
