---
title: /permissive/ (Conformidad de los estándares)
ms.date: 03/08/2019
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: aca0fbc6a2ca36ceae26ba060b5bf92fea79c32c
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273727"
---
# <a name="permissive--standards-conformance"></a>/permissive/ (Conformidad de los estándares)

Especifique el modo de cumplimiento de estándares para el compilador. Use esta opción para ayudarle a identificar y corregir problemas de conformidad en el código, para que sea más correcto y más portátil.

## <a name="syntax"></a>Sintaxis

> **/permissive-**

## <a name="remarks"></a>Comentarios

Esta opción es compatible con Visual Studio 2017 y versiones posteriores.

Puede usar la opción del compilador **/permissive-** para especificar el comportamiento del compilador conforme a los estándares. Esta opción deshabilita los comportamientos permisivas, y establece las opciones del compilador [/ZC](zc-conformance.md) para una compatibilidad estricta. En el IDE, esta opción también hace que el motor de IntelliSense Subraye el código que no es conforme.

De forma predeterminada, la opción **/permissive-** se establece en los nuevos proyectos creados por Visual Studio 2017, versión 15,5 y versiones posteriores. No se establece de forma predeterminada en las versiones anteriores. Cuando se establece la opción, el compilador genera errores o advertencias de diagnóstico cuando se detectan construcciones de lenguaje no estándar en el código, incluidos algunos errores comunes en el código anterior a C + + 11.

La opción **/permissive-** es compatible con casi todos los archivos de encabezado de los kits de Windows más recientes, como el kit de desarrollo de software (SDK) o Windows Driver Kit (WDK), a partir del SDK de Windows Fall Creators (10.0.16299.0). Es posible que las versiones anteriores del SDK no se compilen en **/permissive-** para distintas razones de cumplimiento del código fuente. El compilador y los SDK se distribuyen en diferentes escalas de tiempo de versión, por lo que hay algunos problemas pendientes. Para ver los problemas de archivos de encabezado específicos, vea los siguientes [temas de encabezado de Windows](#windows-header-issues) .

La opción **/permissive-** establece las opciones [/Zc: referenceBinding](zc-referencebinding-enforce-reference-binding-rules.md), [/Zc: strictStrings](zc-strictstrings-disable-string-literal-type-conversion.md)y [/Zc: rvalueCast](zc-rvaluecast-enforce-type-conversion-rules.md) para que cumplan el comportamiento. Estas opciones tienen como valor predeterminado el comportamiento no conforme. Puede pasar opciones **/ZC** específicas después de **/permissive-** en la línea de comandos para invalidar este comportamiento.

En las versiones del compilador a partir de la versión 15,3 de Visual Studio 2017, la opción **/permissive-** establece la opción [/Zc: ternario](zc-ternary.md) . El compilador también implementa más requisitos para la búsqueda de nombres en dos fases. Cuando se establece la opción **/permissive-** , el compilador analiza las definiciones de la plantilla de función y de clase e identifica los nombres dependientes y no dependientes que se usan en las plantillas. En esta versión, solo se realiza el análisis de dependencias de nombre.

Las extensiones específicas del entorno y las áreas de lenguaje que el estándar deja hasta la implementación no se ven afectadas por **/permissive-** . Por ejemplo, el compilador `__declspec`no marca las palabras clave de la Convención de llamada y el control de excepciones estructurado específicas de Microsoft y las directivas o atributos de pragma específicos del compilador en el modo **/permissive-** .

La opción **/permissive-** usa la compatibilidad con la conformidad en la versión actual del compilador para determinar qué construcciones del lenguaje no cumplen las sintaxis. La opción no determina si el código se ajusta a una versión específica del C++ estándar. Para habilitar toda la compatibilidad del compilador implementada con el último borrador estándar, use la opción [/STD: latest](std-specify-language-standard-version.md) . Para restringir la compatibilidad del compilador con el estándar C++ 17 implementado actualmente, use la opción [/STD: c++ 17](std-specify-language-standard-version.md) . Para restringir la compatibilidad del compilador para que coincida mejor con el estándar de C++ 14, use la opción [/STD: c++ 14](std-specify-language-standard-version.md) , que es el valor predeterminado.

No todos los estándares de C++ 11, C++ 14 o C++ 17 admiten el código compatible con el compilador MSVC en todas las versiones de Visual Studio 2017. En función de la versión de Visual Studio, es posible que la opción **/permissive-** no detecte problemas relacionados con algunos aspectos de la búsqueda de nombres en dos fases, el enlace de una referencia no const a un temporal y el tratamiento de Copy init como Direct init, lo que permite varios definidos por el usuario conversiones en inicialización, o tokens alternativos para operadores lógicos y otras áreas de cumplimiento no compatibles. Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md). Para sacar el máximo partido de **/permissive-** , actualice Visual Studio a la versión más reciente.

### <a name="how-to-fix-your-code"></a>Cómo corregir el código

Estos son algunos ejemplos de código que se detecta como no conforme cuando se usa **/permissive-** , junto con las formas sugeridas de corregir los problemas.

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
    f(S); // Hidden friend now found via argument-dependent lookup.
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

En las versiones del compilador anteriores a la versión 15,3 de Visual Studio 2017, el compilador aceptaba argumentos para `?:` el operador condicional (o operador ternario) que el estándar considera ambiguos. En el modo **/permissive-** , el compilador ahora emite uno o más diagnósticos en los casos que se compilan sin diagnósticos en versiones anteriores.

Los errores comunes que pueden ser el resultado de este cambio son:

- error C2593: ' Operator? ' es ambiguo

- error C2679: '? ' binario: no se encontró ningún operador que adopte un operando en la parte derecha del tipo ' B ' (o bien no existe una conversión aceptable)

- error Error c2678: '? ' binario: no se encontró ningún operador que adopte un operando izquierdo de tipo ' A ' (o bien no hay una conversión aceptable)

- error C2446: ': ': no hay conversión de ' B ' a ' a '

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

Existe una excepción importante a este patrón común cuando T representa uno de los tipos de cadena terminada en null (por ejemplo `const char *`, `const char16_t *`,, etc.) y el argumento real a `?:` es un literal de cadena del tipo correspondiente. C++ 17 ha cambiado la semántica de C++ 14. Como resultado, el código del ejemplo 2 se acepta en **/STD: c++ 14** y se rechaza en **/STD: c++ 17** cuando se usa **/Zc: ternario** o **/permissive-** .

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

Otro caso en el que puede ver errores es en operadores condicionales con un argumento `void`de tipo. Este caso puede ser común en las macros similares a las ASERCIONES.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

También puede ver errores en la Metaprogramación de la plantilla, donde los tipos de resultado del operador condicional pueden cambiar en **/Zc: ternario** y **/permissive-** . Una manera de resolver este problema es usar [STD:: remove_reference](../../standard-library/remove-reference-class.md) en el tipo resultante.

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

Cuando se establece la opción **/permissive-** , el compilador analiza las definiciones de la plantilla de función y de clase, identificando los nombres dependientes y dependientes que se usan en las plantillas según sea necesario para la búsqueda de nombres en dos fases. En la versión 15,3 de Visual Studio 2017, se realiza el análisis de dependencias de nombre. En concreto, los nombres no dependientes que no se declaran en el contexto de una definición de plantilla provocan un mensaje C++ de diagnóstico según lo requieran los estándares ISO. En la versión 15,7 de Visual Studio 2017, también se realiza el enlace de nombres no dependientes que requieren una búsqueda dependiente del argumento en el contexto de la definición.

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

Si desea un comportamiento heredado para la búsqueda en dos fases pero, de lo contrario, quiere un comportamiento **/permissive-** , agregue la opción **/Zc: twoPhase-** .

### <a name="windows-header-issues"></a>Problemas de encabezado de Windows

La opción **/permissive-** es demasiado estricta en el caso de las versiones de los kits de Windows anteriores a Windows Fall Creators Update SDK (10.0.16299.0), o a la versión 1709 de Windows Driver Kit (WDK). Se recomienda actualizar a las versiones más recientes de los kits de Windows para poder usar **/permissive-** en el código de controlador de dispositivo o Windows.

Algunos archivos de encabezado del SDK de actualización de Windows de abril de 2018 (10.0.17134.0), el SDK de Windows Fall Creators Update (10.0.16299.0) o el kit para controladores de Windows (WDK) 1709, siguen teniendo problemas que hacen que sean incompatibles con el uso de **/permissive-** . Para solucionar estos problemas, se recomienda restringir el uso de estos encabezados solo a los archivos de código fuente que los requieran y quitar la opción **/permissive-** al compilar los archivos de código fuente específicos.

Estos encabezados de WinRT WRL publicados en el SDK de la actualización de Windows de abril de 2018 (10.0.17134.0) no están limpios con **/permissive-** . Para solucionar estos problemas, no use **/permissive-** , o bien use **/permissive-** con **/Zc: twoPhase-** al trabajar con estos encabezados:

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

Estos encabezados de modo de usuario publicados en el SDK de actualización de Windows de abril de 2018 (10.0.17134.0) no están limpios con **/permissive-** . Para solucionar estos problemas, no use **/permissive-** al trabajar con estos encabezados:

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

   Cuando se usa el modificador de compilador **/permissive-** , la `tagRESTRICTION` estructura no se compila debido al miembro de case (RTOr) ' or '.

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

   Para solucionar este problema, compile archivos que incluyan Query. h sin la opción **/permissive-** .

- Problema en Um/cellularapi_oem. h

   Cuando se usa el modificador de compilador/permissive- `enum UICCDATASTOREACCESSMODE` , la declaración adelantada de genera una advertencia:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   La declaración adelantada de una enumeración sin ámbito es una extensión de Microsoft. Para solucionar este problema, compile archivos que incluyan cellularapi_oem. h sin la opción **/permissive-** o use la opción [/WD](compiler-option-warning-level.md) para silenciar la advertencia C4471.

- Problema en Um/omscript. h

   En C++ 03, una conversión de un literal de cadena a BSTR (que es una definición de tipo en ' wchar_t * ') está en desuso pero se permite. En C++ 11, ya no se permite la conversión.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Para solucionar este problema, compile archivos que incluyan omscript. h sin la opción **/permissive-** o use **/Zc: strictStrings-** en su lugar.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

En la versión 15,5 de Visual Studio 2017 y versiones posteriores, use este procedimiento:

1. Abra el cuadro de diálogo **páginas de propiedades** del proyecto.

1. Seleccione la **Página propiedades** > de configuración**C/C++**  > idioma.

1. Cambie el valor de la propiedad **modo de cumplimiento** a **sí (/permissive-)** . Elija **Aceptar** o **aplicar** para guardar los cambios.

En versiones anteriores a la versión 15,5 de Visual Studio 2017, siga este procedimiento:

1. Abra el cuadro de diálogo **páginas de propiedades** del proyecto.

1. Seleccione la página de propiedades **Propiedades de configuración** > **C/C++**  > **Línea de comandos**.

1. Escriba la opción del compilador **/permissive-** en el cuadro **opciones adicionales** . Elija **Aceptar** o **aplicar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)\
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
