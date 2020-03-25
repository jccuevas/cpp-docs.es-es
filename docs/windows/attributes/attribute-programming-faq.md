---
title: Preguntas más frecuentes de programación con atributos
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 4191704da2fdac849ac1ce97692c2421ba7cda41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168388"
---
# <a name="attribute-programming-faq"></a>Preguntas más frecuentes de programación con atributos

En este tema se responden las siguientes preguntas frecuentes:

- [¿Qué es un valor HRESULT?](#vcconattributeprogrammmingfaqanchor1)

- [¿Cuándo es necesario especificar el nombre del parámetro para un atributo?](#vcconattributeprogrammmingfaqanchor2)

- [¿Puedo usar comentarios en un bloque de atributos?](#vcconattributeprogrammmingfaqanchor3)

- [¿Cómo interactúan los atributos con la herencia?](#vcconattributeprogrammmingfaqanchor4)

- [¿Cómo puedo usar atributos en un proyecto ATL sin atributos?](#vcconattributeprogrammmingfaqanchor5)

- [¿Cómo se puede usar un archivo. idl en un proyecto con atributos?](#vcconattributeprogrammmingfaqanchor6)

- [¿Puedo modificar el código insertado por un atributo?](#vcconattributeprogrammmingfaqanchor7)

- [¿Cómo puedo reenviar declare una interfaz con atributos?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [¿Puedo usar atributos en una clase derivada de una clase que también utiliza atributos?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

##  <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a>¿Qué es un valor HRESULT?

Un valor HRESULT es un tipo de datos simple que se suele usar como valor devuelto por atributos y ATL en general. En la tabla siguiente se describen los distintos valores. Se incluyen más valores en el archivo de encabezado Winerror. h.

|Nombre|Descripción|Value|
|----------|-----------------|-----------|
|S_OK|Operación correcta|0x00000000|
|E_UNEXPECTED|Error inesperado|0x8000FFFF|
|E_NOTIMPL|No implementado|0x80004001|
|E_OUTOFMEMORY|No se pudo asignar la memoria necesaria|0x8007000E|
|E_INVALIDARG|Uno o varios argumentos no son válidos|0x80070057|
|E_NOINTERFACE|No se admite esta interfaz|0x80004002|
|E_POINTER|Puntero no válido|0x80004003|
|E_HANDLE|Identificador no válido|0x80070006|
|E_ABORT|Operación anulada|0x80004004|
|E_FAIL|Error no especificado|0x80004005|
|E_ACCESSDENIED|Error general de acceso denegado|0x80070005|

##  <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a>¿Cuándo es necesario especificar el nombre del parámetro para un atributo?

En la mayoría de los casos, si el atributo tiene un único parámetro, ese parámetro se denomina. Este nombre no es necesario al insertar el atributo en el código. Por ejemplo, el siguiente uso del atributo [agregable](aggregatable.md) :

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

es exactamente igual que:

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

Sin embargo, los siguientes atributos tienen parámetros únicos sin nombre:

||||
|-|-|-|
|[call_as](call-as.md)|[case](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[valor predeterminado](default-cpp.md)|[defaultvalue](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[entry](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[helpfile](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[id](id.md)|
|[iid_is](iid-is.md)|[import](import.md)|[importlib](importlib.md)|
|[include](include-cpp.md)|[includelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[restricted](restricted.md)|
|[size_is](size-is.md)|[de origen](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

##  <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a>¿Puedo usar comentarios en un bloque de atributos?

Puede usar comentarios de una sola línea y de varias líneas dentro de un bloque de atributos. Sin embargo, no puede usar ningún estilo de comentario dentro de los paréntesis que contienen los parámetros a un atributo.

Se permite lo siguiente:

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

No se permite lo siguiente:

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

##  <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a>¿Cómo interactúan los atributos con la herencia?

Puede heredar tanto las clases con atributos como las sin atributos de otras clases, que pueden ser atributos o no. El resultado de derivar de una clase con atributos es el mismo que derivar de esa clase después de que el proveedor de atributos haya transformado su código. Los atributos no se transmiten a las C++ clases derivadas a través de la herencia. Un proveedor de atributos solo transforma el código que está cerca de sus atributos.

##  <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a>¿Cómo puedo usar atributos en un proyecto ATL sin atributos?

Puede tener un proyecto ATL sin atributos, que tiene un archivo. idl, y puede que desee empezar a agregar objetos con atributos. En este caso, use el **Asistente para agregar clases** para proporcionar el código.

##  <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a>¿Cómo se puede usar un archivo. idl en un proyecto con atributos?

Es posible que tenga un archivo. idl que desee usar en el proyecto con atributos ATL. En este caso, usaría el atributo [importidl](importidl.md) , compilará el archivo. idl en un archivo. h (vea las [páginas de propiedades MIDL](../../build/reference/midl-property-pages.md) en el cuadro de diálogo **páginas de propiedades** del proyecto) y, a continuación, incluirá el archivo. h en el proyecto.

##  <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a>¿Puedo modificar el código insertado por un atributo?

Algunos atributos insertan código en el proyecto. Puede ver el código insertado mediante la opción del compilador [/FX](../../build/reference/fx-merge-injected-code.md) . También es posible copiar el código del archivo insertado y pegarlo en el código fuente. Esto le permite modificar el comportamiento del atributo. Sin embargo, es posible que también tenga que modificar otras partes del código.

El ejemplo siguiente es el resultado de copiar el código insertado en un archivo de código fuente:

```cpp
// attr_injected.cpp
// compile with: comsupp.lib
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(name="MyLibrary") ];

// ITestTest
[
   object, uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"), dual, helpstring("ITestTest Interface"), pointer_default(unique)
]

__interface ITestTest : IDispatch {
   [id(1), helpstring("method DoTest")]
   HRESULT DoTest([in] BSTR str);
};

// _ITestTestEvents
[
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"), dispinterface, helpstring("_ITestTestEvents Interface")
]

__interface _ITestTestEvents {
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);
};

// CTestTest
[
   coclass, threading(apartment), vi_progid("TestATL1.TestTest"), progid("TestATL1.TestTest.1"), version(1.0), uuid("D9632007-14FA-4679-9E1C-28C9A949E784"), // this line would be commented out from original file
   // event_source("com"), // this line would be added to support injected code
   source(_ITestTestEvents), helpstring("TestTest Class")
]

class ATL_NO_VTABLE CTestTest : public ITestTest,
// the following base classes support added injected code
public IConnectionPointContainerImpl<CTestTest>,
public IConnectionPointImpl<CTestTest, &__uuidof(::_ITestTestEvents), CComDynamicUnkArray>
{
public:
   CTestTest() {
   }
   // this line would be commented out from original file
   // __event __interface _ITestTestEvents;
   DECLARE_PROTECT_FINAL_CONSTRUCT()
   HRESULT FinalConstruct() {
      return S_OK;
   }

void FinalRelease() {}

public:
   CComBSTR m_value;
   STDMETHOD(DoTest)(BSTR str) {
      VARIANT_BOOL bCancel = FALSE;
      BeforeChange(str,&bCancel);
      if (bCancel) {
          return Error("Error : Someone don't want us to change the value");
      }

   m_value =str;
   return S_OK;
    }
// the following was copied in from the injected code.
HRESULT BeforeChange(::BSTR i1,::VARIANT_BOOL* i2) {
   HRESULT hr = S_OK;
   IConnectionPointImpl<CTestTest, &__uuidof(_ITestTestEvents), CComDynamicUnkArray>* p = this;
   VARIANT rgvars[2];
   Lock();
   IUnknown** pp = p->m_vec.begin();
   Unlock();
   while (pp < p->m_vec.end()) {
      if (*pp != NULL) {
         IDispatch* pDispatch = (IDispatch*) *pp;
         ::VariantInit(&rgvars[1]);
         rgvars[1].vt = VT_BSTR;
         V_BSTR(&rgvars[1])= (BSTR) i1;
         ::VariantInit(&rgvars[0]);
         rgvars[0].vt = (VT_BOOL | VT_BYREF);
         V_BOOLREF(&rgvars[0])= (VARIANT_BOOL*) i2;
         DISPPARAMS disp = { rgvars, NULL, 2, 0 };
         VARIANT ret_val;
         hr = __ComInvokeEventHandler(pDispatch, 1, 1, &disp, &ret_val);
         if (FAILED(hr))
            break;
      }
      pp++;
   }
   return hr;
}

BEGIN_CONNECTION_POINT_MAP(CTestTest)
CONNECTION_POINT_ENTRY(__uuidof(::_ITestTestEvents))
END_CONNECTION_POINT_MAP()
// end added code section

// _ITestCtrlEvents Methods
public:
};

int main() {}
```

##  <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a>¿Cómo puedo reenviar declare una interfaz con atributos?

Si va a crear una declaración adelantada de una interfaz con atributos, debe aplicar los mismos atributos a la declaración adelantada que se aplica a la declaración de interfaz real. También debe aplicar el atributo de [exportación](export.md) a la declaración adelantada.

##  <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a>¿Puedo usar atributos en una clase derivada de una clase que también utiliza atributos?

No, no se admite el uso de atributos en una clase derivada de una clase que también utiliza atributos.

## <a name="see-also"></a>Consulte también

[Atributos de C++ para COM y .NET](cpp-attributes-com-net.md)
