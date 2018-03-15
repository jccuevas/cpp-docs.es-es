---
title: "-permisivo - (cumplimiento de los estándares) | Documentos de Microsoft"
ms.date: 11/11/2016
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
dev_langs:
- C++
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 09b24e96752e61f4d09efc3780e0e60ffed8effd
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="permissive--standards-conformance"></a>/ permisivo-(cumplimiento de los estándares)

Especifique el modo de cumplimiento de normas para el compilador. Utilice esta opción para ayudarle a identificar y corregir los problemas de conformidad en el código, para que sea más portátil y más correcta.

## <a name="syntax"></a>Sintaxis

> **/permissive-**

## <a name="remarks"></a>Comentarios

Puede usar el **/ permisivo-** opción del compilador para especificar el comportamiento del compilador que cumplen los estándares. Esta opción deshabilita comportamientos permisivos y establece el [/Zc](../../build/reference/zc-conformance.md) opciones del compilador para cumplimiento estricto. En el IDE, esta opción también hace que el código que no cumple las especificaciones del subrayado de motor de IntelliSense.

De forma predeterminada, el **/ permisivo-** opción está establecida en proyectos nuevos creados por la versión de Visual Studio de 2017 15,5 y versiones posteriores. No se establece de forma predeterminada en las versiones anteriores. Cuando la opción está establecida, el compilador genera errores de diagnóstico o advertencias al construcciones del lenguaje no estándar se detectan en el código, incluidos algunos errores comunes en pre-código C ++ 11.

El **/ permisivo-** opción es compatible con casi todos los archivos de encabezado de los Kits de Windows más recientes, como el Kit de desarrollo de Software (SDK) o Windows Driver Kit (WDK), a partir del SDK de Windows pertenecen creadores (10.0.16299.0). Pueden producir un error de las versiones anteriores del SDK compilar en **/ permisivo-** para diversas razones de compatibilidad de código de origen. El compilador y el SDK se incluyen en las escalas de tiempo de lanzamiento distintos, por lo tanto, hay algunos problemas restantes. Para problemas de archivo de encabezado específico, consulte [problemas de encabezado de Windows](#windows-header-issues) a continuación.

El **/ permisivo-** opción establece la [/Zc: strictstrings](../../build/reference/zc-conformance.md) y [/Zc: rvaluecast](../../build/reference/zc-conformance.md) opciones para el comportamiento conforme. El valor predeterminado al comportamiento de no conformes. Puede pasar específico **/Zc** opciones después **/ permisivo-** en la línea de comandos para invalidar este comportamiento.

En las versiones del principio de compilador en Visual Studio 2017 versión 15.3, el **/ permisivo-** opción establece la [/Zc:ternary](../../build/reference/zc-ternary.md) opción. El compilador también implementa más de los requisitos para la búsqueda de nombre en dos fases. Cuando el **/ permisivo-** opción está activada, el compilador analiza definiciones de plantilla de función y de clase, identificar dependientes y no dependientes de los nombres utilizados en las plantillas. En esta versión, se realiza solo análisis de dependencias de nombre.

Extensiones específicas del entorno y las áreas de idioma que el estándar deja hasta la implementación no se ven afectadas por **/ permisivo-**. Por ejemplo, específico de Microsoft `__declspec`, convención de llamada y estructurado de excepciones de palabras clave y directivas específicas del compilador pragma o atributos no estén marcados por el compilador en **/ permisivo-** modo.

El **/ permisivo-** opción utiliza la compatibilidad de conformidad en la versión actual del compilador para determinar qué construcciones de lenguaje son no conformes. La opción no determina si el código se ajusta a una versión concreta de C++ estándar. Para habilitar todo el soporte de compilador implementada para el estándar de borrador más reciente, use la [/std:latest](../../build/reference/std-specify-language-standard-version.md) opción. Para restringir la compatibilidad del compilador para la implementada actualmente estándar C ++ 17, utilice la [/std:c ++ 17](../../build/reference/std-specify-language-standard-version.md) opción. Para restringir la compatibilidad del compilador para hacerlos coincidir con el estándar C ++ 14, utilice la [/std:c ++ 14](../../build/reference/std-specify-language-standard-version.md) opción, que es el valor predeterminado.

No todos los C ++ 11, C ++ 14 o C ++ 17 que cumplen los estándares de código es compatible con el compilador de Visual C++ en Visual Studio de 2017. El **/ permisivo-** opción no puede detectar problemas con respecto a algunos aspectos de la búsqueda de nombres en dos fases, enlazar una referencia no const a un archivo temporal, tratar init copia como init directa, lo que permite varias conversiones definidas por el usuario en inicialización o tokens alternativos para los operadores lógicos y otras áreas de conformidad no admitidos. Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="how-to-fix-your-code"></a>Cómo corregir el código

Estos son algunos ejemplos de código que se detecta como no conformes cuando se usa **/ permisivo-**, junto con las formas sugeridos para corregir los problemas.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Usar valor predeterminado como un identificador en el código nativo

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="lookup-members-in-dependent-base"></a>Miembros de búsqueda en base dependiente

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

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Inicializar a varios miembros de la unión de un inicializador de miembro

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

#### <a name="hidden-friend-name-lookup-rules"></a>Oculta las reglas de búsqueda de nombres de confianza

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

#### <a name="use-scoped-enums-in-array-bounds"></a>Usar las enumeraciones de ámbito en los límites de matriz

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Use for each en código nativo

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

En las versiones del compilador antes de Visual Studio 2017 versión 15.3, el compilador acepta argumentos para el operador condicional (o el operador ternario) `?:` que se consideran ambiguos por el estándar. En **/ permisivo-** modo, el compilador emite ahora una o más diagnósticos en casos en que se compiló sin diagnósticos en versiones anteriores.

Errores de Common que pueden derivarse de este cambio se incluyen:

- ¿Error C2593: 'operador'? es ambiguo

- Error C2679: binario '?': encontró ningún un operador que adopte un operando derecho del tipo 'B' (o no hay ninguna conversión aceptable)

- error C2678: binario '?': encontró ningún un operador que adopte un operando izquierdo de tipo 'A' (o no hay ninguna conversión aceptable)

- Error C2446: ':': no hay conversión de 'B' a 'A'

Un modelo de código típico que puede causar este problema es cuando alguna clase C proporciona un constructor no explícita de otro tipo T y un operador de conversión no explícita al tipo T. En este caso, la conversión del argumento 2nd al tipo de los 3 y la conversión del argumento 3rd al tipo de los 2 º son conversiones válidas, que es ambiguo según el estándar.

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

Hay una excepción importante a este patrón común cuando T representa uno de los tipos de cadena terminada en null (por ejemplo, `const char *`, `const char16_t *`, etc.) y el argumento real `?:` es una cadena literal de tipo correspondiente. C ++ 17 ha cambiado la semántica de C ++ 14. Como resultado, se acepta el código de ejemplo 2 en **/std:c ++ 14** y rechazados en **/std:c ++ 17** cuando **/Zc:ternary** o **/permissive-**se utiliza.

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

Otro caso donde puede ver errores es en operadores condicionales con un argumento de tipo `void`. Este caso puede ser habitual en las macros de aserción similar.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

También pueden aparecer errores en plantilla metaprogramación, donde pueden cambiar los tipos de resultado del operador condicional en **/Zc:ternary** y **/ permisivo-**. Una manera de resolver este problema consiste en utilizar [std::remove_reference](../../standard-library/remove-reference-class.md) en el tipo resultante.

```cpp
// Example 4: different result types 
extern bool cond;
extern int count;
char  a = 'A'; 
const char  b = 'B'; 
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary 
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary 
```

#### <a name="two-phase-name-look-up-partial"></a>Buscar nombre en dos fases (parcial)

Cuando el **/ permisivo-** opción está establecida en Visual Studio 2017 versión 15.3, el compilador analiza definiciones de plantilla de función y de clase, identificar dependientes y no dependientes de los nombres utilizados en plantillas según sea necesario para el nombre en dos fases búsqueda. En esta versión, se realiza solo análisis de dependencias de nombre. En concreto, los nombres no dependientes que no se declaran en el contexto de una definición de plantilla que un mensaje de diagnóstico según sea necesario por los estándares ISO C++. Sin embargo, de enlace de nombres no dependientes que requieren argumentos dependientes buscar en el contexto de la definición no se realiza.

```cpp
// dependent base
struct B {
    void g();
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

### <a name="windows-header-issues"></a>Problemas de encabezado de Windows

El **/ permisivo-** opción es demasiado estricta para las versiones de los Kits de Windows antes de Windows pertenecen creadores de actualización SDK (10.0.16299.0) o la versión de Windows Driver Kit (WDK) 1709. Se recomienda actualizar a las versiones más recientes de los Kits de Windows para poder usar **/ permisivo-** en el código de controlador de Windows o dispositivo.

Algunos archivos de encabezado en el SDK de Windows pertenecen creadores de actualización (10.0.16299.0) o Windows Driver Kit (WDK) 1709, tengan problemas que hacerlos incompatibles con el uso de **/ permisivo-**. Para solucionar estos problemas, se recomienda restringir el uso de estos encabezados a solo los archivos de código fuente que necesiten y quitar el **/ permisivo-** opción cuando se compilan los archivos de código fuente específicas. Los problemas siguientes son específicos para el SDK de Windows pertenecen creadores de actualización (10.0.16299.0):

#### <a name="issue-in-umqueryh"></a>Problema en um\Query.h

Cuando se usa el **/ permisivo-** modificador del compilador, el `tagRESTRICTION` estructura no se compila debido a los miembros de case(RTOr) 'o'.

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

Para solucionar este problema, compila los archivos que incluyen Query.h sin el **/ permisivo-** opción.

#### <a name="issue-in-umcellularapioemh"></a>Problema en um\cellularapi_oem.h

Cuando se usa el **/ permisivo-** modificador del compilador, la declaración adelantada de `enum UICCDATASTOREACCESSMODE` da lugar a una advertencia:

```cpp
typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
```

La declaración adelantada de enumeración sin ámbito es una extensión de Microsoft. Para solucionar este problema, compila los archivos que incluyen cellularapi_oem.h sin el **/ permisivo-** opción o usar el [/wd](../../build/reference/compiler-option-warning-level.md) opción Silenciar advertencia C4471.

#### <a name="issue-in-umomscripth"></a>Problema en um\omscript.h

En C ++ 03, una conversión de un literal de cadena a tipo BSTR (que es una definición de tipo para ' wchar_t *') está en desuso pero permitido. En C ++ 11, ya no se permite la conversión.

```cpp
virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
    /* [in] */ __RPC__in BSTR propname,
    /* [in] */ __RPC__in BSTR expression,
    /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
```

Para solucionar este problema, compila los archivos que incluyen omscript.h sin el **/ permisivo-** opción o use **/Zc:strictStrings-** en su lugar.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

En la versión de Visual Studio de 2017 15,5 y versiones posteriores, use este procedimiento:

1. Abra el proyecto **páginas de propiedades** cuadro de diálogo.

1. En **propiedades de configuración**, expanda la **C/C++** carpeta y elija el **lenguaje** página de propiedades.

1. Cambiar el **modo de ajuste** valor de propiedad **Sí (/ permisivo-)**. Elija **Aceptar** o **aplicar** para guardar los cambios.

En las versiones anteriores de Visual Studio 2017 versión 15,5, use este procedimiento:

1. Abra el proyecto **páginas de propiedades** cuadro de diálogo.

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Escriba el **/ permisivo-** opción del compilador en el **opciones adicionales** cuadro. Elija **Aceptar** o **aplicar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)   
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
