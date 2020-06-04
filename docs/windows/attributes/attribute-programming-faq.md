---
title: Preguntas más frecuentes de programación con atributos
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 6c1762994d2cb109e86397bb0a5db1258cf33be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376062"
---
# <a name="attribute-programming-faq"></a>Preguntas más frecuentes de programación con atributos

Este tema responde a las siguientes preguntas frecuentes:

- [¿Qué es un HRESULT?](#vcconattributeprogrammmingfaqanchor1)

- [¿Cuándo tengo que especificar el nombre del parámetro para un atributo?](#vcconattributeprogrammmingfaqanchor2)

- [¿Puedo usar comentarios en un bloque de atributos?](#vcconattributeprogrammmingfaqanchor3)

- [¿Cómo interactúan los atributos con la herencia?](#vcconattributeprogrammmingfaqanchor4)

- [¿Cómo puedo usar atributos en un proyecto ATL no atribuido?](#vcconattributeprogrammmingfaqanchor5)

- [¿Cómo puedo usar un archivo .idl en un proyecto con atributos?](#vcconattributeprogrammmingfaqanchor6)

- [¿Puedo modificar el código que inserta un atributo?](#vcconattributeprogrammmingfaqanchor7)

- [¿Cómo puedo reenviar la declaración de una interfaz con atributos?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [¿Puedo usar atributos en una clase derivada de una clase que también usa atributos?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

## <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a>¿Qué es un HRESULT?

Un HRESULT es un tipo de datos simple que a menudo se utiliza como un valor devuelto por atributos y ATL en general. En la tabla siguiente se describen los distintos valores. Más valores están contenidos en el archivo de encabezado winerror.h.

|Nombre|Descripción|Value|
|----------|-----------------|-----------|
|S_OK|Operación correcta|0x00000000|
|E_UNEXPECTED|Fallo inesperado|0x8000FFFF|
|E_NOTIMPL|No implementado|0x80004001|
|E_OUTOFMEMORY|No se pudo asignar la memoria necesaria|0x8007000E|
|E_INVALIDARG|Uno o más argumentos no son válidos|0x80070057|
|E_NOINTERFACE|No se admite ninguna interfaz de este tipo|0x80004002|
|E_POINTER|Puntero no válido|0x80004003|
|E_HANDLE|Mango no válido|0x80070006|
|E_ABORT|Operación abortada|0x80004004|
|E_FAIL|Fallo no especificado|0x80004005|
|E_ACCESSDENIED|Error de acceso general denegado|0x80070005|

## <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a>¿Cuándo tengo que especificar el nombre del parámetro para un atributo?

En la mayoría de los casos, si el atributo tiene un único parámetro, se denomina ese parámetro. Este nombre no es necesario al insertar el atributo en el código. Por ejemplo, el siguiente uso del atributo [agregable:](aggregatable.md)

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

es exactamente lo mismo que:

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
|[call_as](call-as.md)|[Caso](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[default](default-cpp.md)|[Defaultvalue](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[Entrada](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[Helpfile](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[id](id.md)|
|[iid_is](iid-is.md)|[Importación](import.md)|[importlib](importlib.md)|
|[incluír](include-cpp.md)|[includelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[Restringido](restricted.md)|
|[size_is](size-is.md)|[de origen](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

## <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a>¿Puedo usar comentarios en un bloque de atributos?

Puede utilizar comentarios de una y varias líneas dentro de un bloque de atributos. Sin embargo, no puede utilizar ningún estilo de comentario entre paréntesis que contiene los parámetros en un atributo.

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

## <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a>¿Cómo interactúan los atributos con la herencia?

Puede heredar clases con atributos y no atribuidos de otras clases, que pueden atribuirse o no. El resultado de derivar de una clase con atributos es el mismo que derivar de esa clase después de que el proveedor de atributos haya transformado su código. Los atributos no se transmiten a clases derivadas a través de la herencia C++. Un proveedor de atributos solo transforma el código en las proximidades de sus atributos.

## <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a>¿Cómo puedo usar atributos en un proyecto ATL no atribuido?

Es posible que tenga un proyecto ATL no atribuido, que tiene un archivo .idl, y es posible que desee empezar a agregar objetos con atributos. En este caso, use el **Asistente para agregar clases** para proporcionar el código.

## <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a>¿Cómo puedo usar un archivo .idl en un proyecto con atributos?

Es posible que tenga un archivo .idl que desea usar en el proyecto con atributos ATL. En este caso, usaría el atributo [importidl,](importidl.md) compilaría el archivo .idl en un archivo .h (consulte las páginas de propiedades [MIDL](../../build/reference/midl-property-pages.md) en el cuadro de diálogo **Páginas** de propiedades del proyecto) y, a continuación, incluiría el archivo .h en el proyecto.

## <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a>¿Puedo modificar el código que inserta un atributo?

Algunos atributos insertan código en el proyecto. Puede ver el código insertado mediante la opción del compilador [/Fx.](../../build/reference/fx-merge-injected-code.md) También es posible copiar código del archivo inyectado y pegarlo en el código fuente. Esto le permite modificar el comportamiento del atributo. Sin embargo, es posible que también tenga que modificar otras partes del código.

El ejemplo siguiente es el resultado de copiar el código inyectado en un archivo de código fuente:

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

## <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a>¿Cómo puedo reenviar la declaración de una interfaz con atributos?

Si va a realizar una declaración de reenvío de una interfaz con atributos, debe aplicar los mismos atributos a la declaración de reenvío que se aplica a la declaración de interfaz real. También debe aplicar el atributo [export](export.md) a la declaración de reenvío.

## <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a>¿Puedo usar atributos en una clase derivada de una clase que también usa atributos?

No, no se admite el uso de atributos en una clase derivada de una clase que también utiliza atributos.

## <a name="see-also"></a>Consulte también

[Atributos de C++ para COM y .NET](cpp-attributes-com-net.md)
