---
title: com::ptr (Clase)
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::com::ptr::ptr
- msclr::com::ptr::Attach
- msclr::com::ptr::CreateInstance
- msclr::com::ptr::Detach
- msclr::com::ptr::GetInterface
- msclr::com::ptr::QueryInterface
- msclr::com::ptr::Release
- msclr::com::ptr::operator=
- msclr::com::ptr::operator->
- msclr::com::ptr::operator!
helpviewer_keywords:
- msclr::ptr class
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
ms.openlocfilehash: 342c222b837e179e2e13dbbd27c88efc18b12332
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774178"
---
# <a name="comptr-class"></a>com::ptr (Clase)

Un contenedor para un objeto COM que se puede usar como un miembro de una clase CLR.  El contenedor también automatiza la administración de la duración del objeto COM, liberar la propiedad de todas las referencias en el objeto cuando se llama a su destructor. Análoga a [clase CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Sintaxis

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Parámetros

*_interface_type*<br/>
Interfaz COM.

## <a name="remarks"></a>Comentarios

Un `com::ptr` también puede utilizarse como una variable de la función local para simplificar las diversas tareas de COM y automatizar la administración de la duración.

Un `com::ptr` no se puede usar directamente como un parámetro de función; utilice un [operador de referencia de seguimiento](../extensions/tracking-reference-operator-cpp-component-extensions.md) o un [identificador de operador de objeto (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) en su lugar.

Un `com::ptr` no se puede devolver directamente desde una función; utilice un identificador en su lugar.

## <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto.  Llamar a los métodos públicos de los resultados de la clase en las llamadas a los contenidos `IXMLDOMDocument` objeto.  El ejemplo crea una instancia de un documento XML, lo rellena con algo de XML simple y un tutorial simplificado de los nodos en el árbol de documento analizado para imprimir el XML en la consola.

```cpp
// comptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into the document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // simplified function to write just the first xml node to the console
   void WriteXml() {
      IXMLDOMNode* pNode = NULL;

      try {
         // the first child of the document is the first real xml node
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            WriteNode(pNode);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(IXMLDOMNode* pNode) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteXml();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<word>persnickety</word>
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción| 
|---------|-----------| 
|[ptr::ptr](#ptr)|Construye un `com::ptr` para encapsular un objeto COM.| 
|[ptr::~ptr](#tilde-ptr)|Destructs un `com::ptr`.| 

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|---------|-----------| 
|[ptr::Attach](#attach)|Adjunta un objeto COM para un `com::ptr`.| 
|[ptr::CreateInstance](#createInstance)|Crea una instancia de un objeto COM dentro de un `com::ptr`.| 
|[ptr::Detach](#detach)|Interrumpe la propiedad del objeto COM, devuelve un puntero al objeto.| 
|[ptr::GetInterface](#getInterface)|Crea una instancia de un objeto COM dentro de un `com::ptr`.| 
|[ptr::QueryInterface](#queryInterface)|Consulta al objeto COM que se poseen una interfaz y adjunta el resultado a otro `com::ptr`.| 
|[ptr::Release](#release)|Libera todas las referencias de propiedad en el objeto COM.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|---------|-----------| 
|[ptr::operator-&gt;](#operator-arrow)|Operador de acceso a miembro, se usa para llamar a métodos en el objeto COM que se poseen.| 
|[ptr::operator=](#operator-assign)|Adjunta un objeto COM para un `com::ptr`.| 
|[ptr::operator&nbsp;bool](#operator-bool)|Operador para el uso de `com::ptr` en una expresión condicional.| 
|[ptr::operator!](#operator-logical-not)|Operador para determinar si el objeto COM que se poseen no es válido.| 

## <a name="requirements"></a>Requisitos

**Archivo de encabezado** \<msclr\com\ptr.h >

**Namespace** msclr::com

 

## <a name="ptr"></a>ptr::ptr

Devuelve un puntero al objeto COM que se poseen.

```cpp
ptr();
ptr(
   _interface_type * p
);
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a interfaz COM.

### <a name="remarks"></a>Comentarios

El constructor sin argumentos asigna `nullptr` para el identificador del objeto subyacente. Las llamadas futuras a la `com::ptr` validará el objeto interno y se produce un error silencioso hasta que se crea o se adjunta un objeto.

El constructor de un argumento agrega una referencia al objeto COM pero no libera la referencia del llamador, por lo que el llamador debe llamar a `Release` en el objeto COM para realmente ceder el control. Cuando el `com::ptr`del se llama al destructor liberará automáticamente sus referencias en el objeto COM.

Pasar `NULL` a este constructor es igual que llamar a la versión sin argumentos.

### <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto. Muestra el uso de ambas versiones del constructor.

```cpp
// comptr_ptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="tilde-ptr"></a>ptr::~ptr

Destructs un `com::ptr`.

```cpp
~ptr();
```

### <a name="remarks"></a>Comentarios

En la destrucción, el `com::ptr` libera todas las referencias posee a su objeto COM. Suponiendo que no hay ninguna otra referencia contenida en el objeto COM, se eliminará el objeto COM y liberar su memoria.

### <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto.  En el `main` (función), los dos `XmlDocument` destructores de los objetos que se llamará cuando salen del ámbito de la `try` bloque, lo que resulta en subyacente `com::ptr` destructor que se llama, liberar la propiedad de todas las referencias a COM objeto.

```cpp
// comptr_dtor.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="attach"></a>ptr::Attach

Adjunta un objeto COM para un `com::ptr`.

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parámetros

*_right*<br/>
El puntero de interfaz COM para adjuntar.

### <a name="exceptions"></a>Excepciones

Si el `com::ptr` ya posee una referencia a un objeto COM, `Attach` produce <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Comentarios

Una llamada a `Attach` hace referencia al objeto COM pero no libera la referencia del llamador.

Pasar `NULL` a `Attach` da como resultado que se va a realizar ninguna acción.

### <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto. El `ReplaceDocument` llama primero a la función de miembro `Release` en cualquier anteriormente pertenecían a objeto y, a continuación, llama a `Attach` para adjuntar un nuevo objeto de documento.

```cpp
// comptr_attach.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="createInstance"></a>ptr::CreateInstance

Crea una instancia de un objeto COM dentro de un `com::ptr`.

```cpp
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   System::String ^ progid
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   const wchar_t * progid
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter
);
void CreateInstance(
   REFCLSID rclsid
);
```

### <a name="parameters"></a>Parámetros

*progid*<br/>
Cadena de `ProgID`.

*pouter*<br/>
Puntero a interfaz de IUnknown del objeto agregado (IUnknown de control). Si `pouter` no se especifica, `NULL` se utiliza.

*cls_context*<br/>
Contexto en que se ejecutará el código que administra el objeto recién creado. Los valores se toman de la `CLSCTX` enumeración. Si `cls_context` no se especifica, el valor se usa CLSCTX_ALL.

*rclsid*<br/>
`CLSID` asociado con los datos y el código que se usará para crear el objeto.

### <a name="exceptions"></a>Excepciones

Si el `com::ptr` ya posee una referencia a un objeto COM, `CreateInstance` produce <xref:System.InvalidOperationException>.

Esta función llama a `CoCreateInstance` y usa <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> para convertir cualquier error `HRESULT` a una excepción adecuada.

### <a name="remarks"></a>Comentarios

`CreateInstance` usa `CoCreateInstance` para crear una nueva instancia del objeto especificado, identificado desde un ProgID o CLSID. El `com::ptr` hace referencia al objeto recién creado y liberará automáticamente las referencias de todos los que se poseen tras la destrucción.

### <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto. Los constructores de clase utilizan dos formas diferentes de `CreateInstance` para crear el objeto de documento desde un ProgID o CLSID además un CLSCTX.

```cpp
// comptr_createinstance.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }
   XmlDocument(REFCLSID clsid, DWORD clsctx) {
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc1("Msxml2.DOMDocument.3.0");

      // or from a clsid with specific CLSCTX
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

## <a name="detach"></a>ptr::Detach

Interrumpe la propiedad del objeto COM, devuelve un puntero al objeto.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto COM.

Si no es propiedad de ningún objeto, se devuelve NULL.

### <a name="exceptions"></a>Excepciones

Internamente, `QueryInterface` se llama en el objeto COM que se poseen y cualquier error `HRESULT` se convierte en una excepción por <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Comentarios

`Detach` en primer lugar, agrega una referencia al objeto COM en nombre del llamador y, a continuación, libera todas las referencias que pertenecen a la `com::ptr`.  El llamador debe liberar en última instancia, el objeto devuelto para destruirlo.

### <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto.  El `DetachDocument` función miembro llama a `Detach` renunciar a la propiedad del objeto COM y devolver un puntero al llamador.

```cpp
// comptr_detach.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // detach the COM object and return it
   // this releases the internal reference to the object
   IXMLDOMDocument* DetachDocument() {
      return m_ptrDoc.Detach();
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.DetachDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release document object as the ref class no longer owns it
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

## <a name="getInterface"></a>ptr::GetInterface

Devuelve un puntero al objeto COM que se poseen.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto COM que se poseen.

### <a name="exceptions"></a>Excepciones

Internamente, `QueryInterface` se llama en el objeto COM que se poseen y cualquier error `HRESULT` se convierte en una excepción por <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Comentarios

El `com::ptr` agrega una referencia al objeto COM en nombre del llamador y también mantiene su propia referencia en el objeto COM. El llamador debe liberar en última instancia, la referencia en el objeto devuelto o nunca se destruirá.

### <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto. El `GetDocument` usa la función miembro `GetInterface` para devolver un puntero al objeto COM.

```cpp
// comptr_getinterface.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
            String^ strName = gcnew String(bstr);
            Console::Write("<{0}>", strName);
            ::SysFreeString(bstr);
            bstr = NULL;

            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
            Console::Write(gcnew String(bstr));
            ::SysFreeString(bstr);
            bstr = NULL;

            Console::WriteLine("</{0}>", strName);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

```Output
<word>persnickety</word>
```

## <a name="queryInterface"></a>ptr::QueryInterface

Consulta al objeto COM que se poseen una interfaz y adjunta el resultado a otro `com::ptr`.

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Parámetros

*other*<br/>
El `com::ptr` que obtendrá la interfaz.

### <a name="exceptions"></a>Excepciones

Internamente, `QueryInterface` se llama en el objeto COM que se poseen y cualquier error `HRESULT` se convierte en una excepción por <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Comentarios

Utilice este método para crear un contenedor COM para una interfaz diferente del objeto COM que son propiedad del contenedor actual. Este método llama a `QueryInterface` a través del objeto COM que se poseen para solicitar un puntero a una interfaz de COM específica de objetos y adjunta el puntero de interfaz devuelto a en el pasado `com::ptr`.

### <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto. El `WriteTopLevelNode` usa la función miembro `QueryInterface` para rellenar una variable local `com::ptr` con un `IXMLDOMNode` y, a continuación, pasa el `com::ptr` (mediante el seguimiento de referencia) a una función de miembro privado que escribe el nombre y texto de las propiedades de nodo en la consola.

```cpp
// comptr_queryinterface.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into our document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // write the top level node to the console
   void WriteTopLevelNode() {
      com::ptr<IXMLDOMNode> ptrNode;

      // query for the top level node interface
      m_ptrDoc.QueryInterface(ptrNode);
      WriteNode(ptrNode);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(com::ptr<IXMLDOMNode> % node) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(node->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(node->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteTopLevelNode();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<#document>persnickety</#document>
```

## <a name="release"></a>ptr::Release

Libera todas las referencias de propiedad en el objeto COM.

```cpp
void Release();
```

### <a name="remarks"></a>Comentarios

Llamar a esta función libera todos los que se poseen las referencias en el objeto COM y establece el identificador interno para el objeto COM `nullptr`.  Si no hay otras referencias en el objeto COM existen, se destruirá.

### <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto.  El `ReplaceDocument` usa la función miembro `Release` para liberar cualquier objeto de documento anterior antes de conectar el nuevo documento.

```cpp
// comptr_release.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="operator-arrow"></a>ptr::operator-&gt;

Operador de acceso a miembro, se usa para llamar a métodos en el objeto COM que se poseen.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Valor devuelto

Un `smart_com_ptr` al objeto COM.

### <a name="exceptions"></a>Excepciones

Internamente, `QueryInterface` se llama en el objeto COM que se poseen y cualquier error `HRESULT` se convierte en una excepción por <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Comentarios

Este operador permite llamar a métodos del objeto COM que se poseen. Devuelve un archivo temporal `smart_com_ptr` que automáticamente controla su propio `AddRef` y `Release`.

### <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto. El `WriteDocument` función usa `operator->` para llamar a la `get_firstChild` miembro del objeto de documento.

```cpp
// comptr_op_member.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
            String^ strName = gcnew String(bstr);
            Console::Write("<{0}>", strName);
            ::SysFreeString(bstr);
            bstr = NULL;

            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
            Console::Write(gcnew String(bstr));
            ::SysFreeString(bstr);
            bstr = NULL;

            Console::WriteLine("</{0}>", strName);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

```Output
<word>persnickety</word>
```

## <a name="operator-assign"></a>ptr::operator=

Adjunta un objeto COM para un `com::ptr`.

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parámetros

*_right*<br/>
El puntero de interfaz COM para adjuntar.

### <a name="return-value"></a>Valor devuelto

Una referencia de seguimiento en el `com::ptr`.

### <a name="exceptions"></a>Excepciones

Si el `com::ptr` ya posee una referencia a un objeto COM, `operator=` produce <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Comentarios

Asignación de un objeto COM para un `com::ptr` hace referencia al objeto COM pero no libera la referencia del llamador.

Este operador tiene el mismo efecto que `Attach`.

### <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto.  El `ReplaceDocument` llama primero a la función de miembro `Release` en cualquier anteriormente pertenecían a objeto y, a continuación, usa `operator=` para adjuntar un nuevo objeto de documento.

```cpp
// comptr_op_assign.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc = pDoc;
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by the ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="operator-bool"></a> ptr::operator bool

Operador para el uso de `com::ptr` en una expresión condicional.

```cpp
operator bool();
```

### <a name="return-value"></a>Valor devuelto

`true` Si es válido; el objeto COM que se poseen `false` en caso contrario.

### <a name="remarks"></a>Comentarios

Es válido si no es el objeto COM que se poseen `nullptr`.

Este operador convierte a `_detail_class::_safe_bool` que es más seguro que `bool` porque no se puede convertir a un tipo entero.

### <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto. El `CreateInstance` usa la función miembro `operator bool` después de crear el nuevo objeto de documento para determinar si es válido y escribe en la consola si lo es.

```cpp
// comptr_op_bool.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) { // uses operator bool
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```

## <a name="operator-logical-not"></a>ptr::operator!

Operador para determinar si el objeto COM que se poseen no es válido.

```cpp
bool operator!();
```

### <a name="return-value"></a>Valor devuelto

`true` Si no es válido; el objeto COM que se poseen `false` en caso contrario.

### <a name="remarks"></a>Comentarios

Es válido si no es el objeto COM que se poseen `nullptr`.

### <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto.  El `CreateInstance` usa la función miembro `operator!` para determinar si un objeto de documento ya tiene propietario y solo crea una nueva instancia si el objeto no es válido.

```cpp
// comptr_op_not.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) {
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```
