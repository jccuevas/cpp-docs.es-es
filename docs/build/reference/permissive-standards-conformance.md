---
title: /permissive/ (Conformidad de los estándares)
description: Guía de referencia de la opción del compilador/permissive-(cumplimiento de estándares) de Microsoft C++.
ms.date: 06/04/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 3b5ddc4b4e9b70b2191a17d2201a441603182149
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84507032"
---
# <a name="permissive--standards-conformance"></a>/permissive/ (Conformidad de los estándares)

Especifique el modo de cumplimiento de estándares para el compilador. Use esta opción para ayudarle a identificar y corregir problemas de conformidad en el código, para que sea más correcto y más portátil.

## <a name="syntax"></a>Sintaxis

> **`/permissive-`**

## <a name="remarks"></a>Comentarios

Esta opción es compatible con Visual Studio 2017 y versiones posteriores.

Puede usar la **`/permissive-`** opción del compilador para especificar el comportamiento del compilador conforme a los estándares. Esta opción deshabilita los comportamientos permisivas, y establece las [**`/Zc`**](zc-conformance.md) Opciones del compilador para que el cumplimiento sea estricto. En el IDE, esta opción también hace que el motor de IntelliSense Subraye el código que no es conforme.

De forma predeterminada, la **`/permissive-`** opción se establece en los proyectos nuevos creados por Visual Studio 2017 versión 15,5 y versiones posteriores. No está establecida de forma predeterminada en versiones anteriores. Cuando se establece la opción, el compilador genera errores de diagnóstico o advertencias cuando se detectan construcciones de lenguaje no estándar en el código. Estas construcciones incluyen algunos errores comunes en el código anterior a C + + 11.

La **`/permissive-`** opción es compatible con casi todos los archivos de encabezado de los kits de Windows más recientes, como el kit de desarrollo de software (SDK) o Windows Driver Kit (WDK), a partir del SDK de Windows Fall Creators (10.0.16299.0). Es posible que las versiones anteriores del SDK no se puedan compilar en **`/permissive-`** por diversos motivos de cumplimiento del código fuente. El compilador y los SDK se distribuyen en diferentes escalas de tiempo de lanzamiento, por lo que hay algunos problemas pendientes. Para ver los problemas de archivos de encabezado específicos, vea los siguientes [temas de encabezado de Windows](#windows-header-issues) .

La **`/permissive-`** opción establece las [**`/Zc:referenceBinding`**](zc-referencebinding-enforce-reference-binding-rules.md) [**`/Zc:strictStrings`**](zc-strictstrings-disable-string-literal-type-conversion.md) Opciones, y [**`/Zc:rvalueCast`**](zc-rvaluecast-enforce-type-conversion-rules.md) para que el comportamiento sea compatible. Estas opciones tienen como valor predeterminado el comportamiento no conforme. Puede pasar opciones específicas **`/Zc`** después **`/permissive-`** de en la línea de comandos para invalidar este comportamiento.

En las versiones del compilador a partir de la versión 15,3 de Visual Studio 2017, la **`/permissive-`** opción establece la [**`/Zc:ternary`**](zc-ternary.md) opción. El compilador también implementa más requisitos para la búsqueda de nombres en dos fases. Cuando **`/permissive-`** se establece la opción, el compilador analiza las definiciones de la plantilla de función y de clase e identifica los nombres dependientes y dependientes que se usan en las plantillas. En esta versión, solo se realiza el análisis de dependencias de nombre.

Las extensiones específicas del entorno y las áreas de lenguaje que el estándar deja hasta la implementación no se ven afectadas por **`/permissive-`** . Por ejemplo, el `__declspec` compilador en modo no marca las palabras clave de la Convención de llamada y el control de excepciones estructurado específicas de Microsoft, ni de directivas o atributos de pragma específicos del compilador **`/permissive-`** .

La **`/permissive-`** opción utiliza la compatibilidad con la conformidad en la versión actual del compilador para determinar qué construcciones del lenguaje no cumplen las sintaxis. La opción no determina si el código se ajusta a una versión específica del estándar de C++. Para habilitar toda la compatibilidad del compilador implementada con el último borrador estándar, use la [**`/std:c++latest`**](std-specify-language-standard-version.md) opción. Para restringir la compatibilidad del compilador con el estándar C++ 17 implementado actualmente, use la [**`/std:c++17`**](std-specify-language-standard-version.md) opción. Para restringir la compatibilidad del compilador para que coincida mejor con el estándar de C++ 14, use la [**`/std:c++14`**](std-specify-language-standard-version.md) opción, que es el valor predeterminado.

No todos los estándares de C++ 11, C++ 14 o C++ 17 admiten el código compatible con el compilador MSVC en todas las versiones de Visual Studio 2017. En función de la versión de Visual Studio, **`/permissive-`** es posible que la opción no detecte problemas en algunos aspectos de la búsqueda de nombres en dos fases, el enlace de una referencia no const a una temporal, tratando la copia init como Direct init, lo que permite varias conversiones definidas por el usuario en la inicialización, o tokens alternativos para operadores lógicos y otras áreas de cumplimiento no compatibles Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md). Para sacar el máximo partido de **`/permissive-`** , actualice Visual Studio a la versión más reciente.

### <a name="how-to-fix-your-code"></a>Cómo corregir el código

Estos son algunos ejemplos de código que se detecta como no conforme al usar **`/permissive-`** , junto con las formas sugeridas de corregir los problemas.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Usar default como identificador en código nativo

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>Buscar miembros en base dependiente

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>Uso de nombres completos en declaraciones de miembros

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Inicializar varios miembros de Unión en un inicializador de miembro

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

#### <a name="hidden-friend-name-lookup-rules"></a>Reglas de búsqueda de nombres Friend ocultas

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

#### <a name="use-scoped-enums-in-array-bounds"></a>Usar enumeraciones con ámbito en los límites de la matriz

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Usar para cada en código nativo

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

#### <a name="ambiguous-conditional-operator-arguments"></a>Argumentos de operador condicional ambiguos

En las versiones del compilador anteriores a la versión 15,3 de Visual Studio 2017, el compilador aceptaba argumentos para el operador condicional (o operador ternario) `?:` que el estándar considera ambiguos. En **`/permissive-`** el modo, el compilador ahora emite uno o más diagnósticos en los casos que se compilan sin diagnósticos en versiones anteriores.

Los errores comunes que pueden ser el resultado de este cambio son:

- **`error C2593`**`: 'operator ?' is ambiguous`

- **`error C2679`**`: binary '?': no operator found which takes a right-hand operand of type 'B' (or there is no acceptable conversion)`

- **`error C2678`**`: binary '?': no operator found which takes a left-hand operand of type 'A' (or there is no acceptable conversion)`

- **`error C2446`**`: ':': no conversion from 'B' to 'A'`

Un patrón de código típico que puede provocar este problema es cuando una clase C proporciona tanto un constructor no explícito de otro tipo T como un operador de conversión no explícito al tipo T. En este caso, la conversión del segundo argumento al tipo del tercer argumento, y la conversión del tercer argumento al tipo del segundo argumento, son conversiones válidas. Puesto que ambos son válidos, es ambiguo según el estándar.

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

Existe una excepción importante a este patrón común cuando T representa uno de los tipos de cadena terminada en null (por ejemplo, `const char *` , `const char16_t *` , etc.) y el argumento real a `?:` es un literal de cadena del tipo correspondiente. C++ 17 ha cambiado la semántica de C++ 14. Como resultado, el código del ejemplo 2 se acepta y se **`/std:c++14`** rechaza en **`/std:c++17`** cuando **`/Zc:ternary`** **`/permissive-`** se usa o.

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

Otro caso en el que puede ver errores es en operadores condicionales con un argumento de tipo **`void`** . Este caso puede ser común en las macros similares a las ASERCIONES.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

También puede ver errores en la Metaprogramación de la plantilla, donde los tipos de resultado del operador condicional pueden cambiar en **`/Zc:ternary`** y **`/permissive-`** . Una manera de resolver este problema es usar [`std::remove_reference`](../../standard-library/remove-reference-class.md) en el tipo resultante.

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

Cuando **`/permissive-`** se establece la opción, el compilador analiza las definiciones de la plantilla de función y de clase, identificando los nombres dependientes y dependientes que se usan en las plantillas según sea necesario para la búsqueda de nombres en dos fases. En la versión 15,3 de Visual Studio 2017, se realiza el análisis de dependencias de nombre. En concreto, los nombres no dependientes que no se declaran en el contexto de una definición de plantilla provocan un mensaje de diagnóstico según lo requieran los estándares ISO de C++. En la versión 15,7 de Visual Studio 2017, también se realiza el enlace de nombres no dependientes que requieren una búsqueda dependiente del argumento en el contexto de la definición.

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

Si desea un comportamiento heredado para la búsqueda en dos fases pero, en caso contrario **`/permissive-`** , desea un comportamiento, agregue la **`/Zc:twoPhase-`** opción.

### <a name="windows-header-issues"></a>Problemas de encabezado de Windows

La **`/permissive-`** opción es demasiado estricta en el caso de las versiones de los kits de Windows anteriores al SDK de Windows Fall Creators Update (10.0.16299.0) o a la versión 1709 de Windows Driver Kit (WDK). Se recomienda actualizar a las versiones más recientes de los kits de Windows que se usarán **`/permissive-`** en el código de controlador de dispositivo o Windows.

Algunos archivos de encabezado del SDK de Windows de abril de 2018 (10.0.17134.0), Windows Fall Creators Update SDK (10.0.16299.0) o Windows Driver Kit (WDK) 1709, siguen teniendo problemas que hacen que sean incompatibles con el uso de **`/permissive-`** . Para solucionar estos problemas, se recomienda restringir el uso de estos encabezados solo a los archivos de código fuente que los requieran y quitar la **`/permissive-`** opción al compilar los archivos de código fuente específicos.

Estos encabezados de WinRT WRL publicados en el SDK de la actualización de Windows de abril de 2018 (10.0.17134.0) no están limpios con **`/permissive-`** . Para solucionar estos problemas, no use **`/permissive-`** o use **`/permissive-`** con **`/Zc:twoPhase-`** cuando trabaje con estos encabezados:

- Problemas en winrt/WRL/Async. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Problema en winrt/WRL/Implements. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Estos encabezados de modo de usuario publicados en el SDK de actualización de Windows de abril de 2018 (10.0.17134.0) no están limpios con **`/permissive-`** . Para solucionar estos problemas, no use **`/permissive-`** al trabajar con estos encabezados:

- Problemas de um/Tune. h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Problema en Um/spddkhlp. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Problemas de um/refptrco. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Estos problemas son específicos de los encabezados de modo de usuario en el SDK de Windows Fall Creators Update (10.0.16299.0):

- Problema en Um/Query. h

   Cuando se usa el **`/permissive-`** modificador de compilador, la `tagRESTRICTION` estructura no se compila debido al miembro de case (RTOr) ' or '.

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

   Para solucionar este problema, compile archivos que incluyan Query. h sin la **`/permissive-`** opción.

- Problema en Um/cellularapi_oem. h

   Al utilizar el **`/permissive-`** modificador de compilador, la declaración adelantada de `enum UICCDATASTOREACCESSMODE` genera una advertencia:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   La declaración adelantada de una enumeración sin ámbito es una extensión de Microsoft. Para solucionar este problema, compile archivos que incluyan cellularapi_oem. h sin la **`/permissive-`** opción o use la [**`/wd`**](compiler-option-warning-level.md) opción para silenciar la advertencia C4471.

- Problema en Um/omscript. h

   En C++ 03, una conversión de un literal de cadena a BSTR (que es una definición de tipo como ' wchar_t * ') está en desuso pero se permite. En C++ 11, ya no se permite la conversión.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Para solucionar este problema, compile archivos que incluyan omscript. h sin la **`/permissive-`** opción, o use **`/Zc:strictStrings-`** en su lugar.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

En la versión 15,5 de Visual Studio 2017 y versiones posteriores, use este procedimiento:

1. Abra el cuadro de diálogo **páginas de propiedades** del proyecto.

1. Seleccione la página **propiedades de configuración**del  >  **lenguaje C/C++**  >  **Language** .

1. Cambie el valor de la propiedad **modo de cumplimiento** a **sí (/permissive-)**. Elija **Aceptar** o **aplicar** para guardar los cambios.

En versiones anteriores a la versión 15,5 de Visual Studio 2017, siga este procedimiento:

1. Abra el cuadro de diálogo **páginas de propiedades** del proyecto.

1. Seleccione la **Configuration Properties**página de propiedades línea de comandos de  >  **C/C++** de propiedades de configuración  >  **Command Line** .

1. Escriba la opción del compilador **/permissive-** en el cuadro **opciones adicionales** . Elija **Aceptar** o **aplicar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte también:

[Opciones del compilador MSVC](compiler-options.md)\
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
