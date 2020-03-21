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
ms.openlocfilehash: 8a3223543dfa6c1b5b45fef2780cd11b558eab84
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078965"
---
# <a name="comptr-class"></a>com::ptr (Clase)

Contenedor de un objeto COM que se puede utilizar como miembro de una clase de CLR.  El contenedor también automatiza la administración de la duración del objeto COM, liberando todas las referencias de propiedad en el objeto cuando se llama a su destructor. Análogo a la [Clase CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Sintaxis

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Parámetros

*_interface_type*<br/>
Interfaz COM.

## <a name="remarks"></a>Observaciones

También se puede utilizar un `com::ptr` como variable de función local para simplificar varias tareas COM y automatizar la administración de la duración.

No se puede usar un `com::ptr` directamente como parámetro de función; en su lugar, use un [operador de referencia de seguimiento](../extensions/tracking-reference-operator-cpp-component-extensions.md) o un [identificador para el operador de objeto (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) .

No se puede devolver un `com::ptr` directamente desde una función; Use un identificador en su lugar.

## <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto.  Llamar a los métodos públicos de la clase produce llamadas al objeto `IXMLDOMDocument` contenido.  En el ejemplo se crea una instancia de un documento XML, se llena con algún XML simple y se realiza un recorrido simplificado de los nodos del árbol del documento analizado para imprimir el XML en la consola.

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

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|---------|-----------|
|[ptr::ptr](#ptr)|Construye un `com::ptr` para encapsular un objeto COM.|
|[ptr::~ptr](#tilde-ptr)|Destruye un `com::ptr`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|---------|-----------|
|[ptr::Attach](#attach)|Adjunta un objeto COM a un `com::ptr`.|
|[ptr::CreateInstance](#createInstance)|Crea una instancia de un objeto COM dentro de un `com::ptr`.|
|[ptr::Detach](#detach)|Proporciona la propiedad del objeto COM y devuelve un puntero al objeto.|
|[ptr::GetInterface](#getInterface)|Crea una instancia de un objeto COM dentro de un `com::ptr`.|
|[ptr::QueryInterface](#queryInterface)|Consulta el objeto COM de propiedad de una interfaz y asocia el resultado a otro `com::ptr`.|
|[ptr::Release](#release)|Libera todas las referencias propiedad del objeto COM.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|---------|-----------|
|[PTR:: Operator-&gt;](#operator-arrow)|Operador de acceso a miembros, que se usa para llamar a métodos en el objeto COM de propiedad.|
|[ptr::operator=](#operator-assign)|Adjunta un objeto COM a un `com::ptr`.|
|[PTR:: Operator&nbsp;bool](#operator-bool)|Operador para usar `com::ptr` en una expresión condicional.|
|[ptr::operator!](#operator-logical-not)|Para determinar si el objeto COM de propiedad no es válido.|

## <a name="requirements"></a>Requisitos

**Archivo de encabezado** \<msclr\com\ptr.h >

**Espacio de nombres** msclr:: com

## <a name="ptrptr"></a><a name="ptr"></a>PTR::p TR

Devuelve un puntero al objeto COM de propiedad.

```cpp
ptr();
ptr(
   _interface_type * p
);
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a interfaz COM.

### <a name="remarks"></a>Observaciones

El constructor sin argumentos asigna `nullptr` al identificador de objeto subyacente. Las futuras llamadas al `com::ptr` validarán el objeto interno y producirán un error de forma silenciosa hasta que se cree o adjunte un objeto.

El constructor de un argumento agrega una referencia al objeto COM, pero no libera la referencia del llamador, por lo que el llamador debe llamar a `Release` en el objeto COM para ofrecer realmente el control. Cuando se llama al destructor del `com::ptr`, liberará automáticamente sus referencias en el objeto COM.

Pasar `NULL` a este constructor es igual que llamar a la versión sin argumentos.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto. Muestra el uso de ambas versiones del constructor.

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

## <a name="ptrptr"></a><a name="tilde-ptr"></a>PTR:: ~ PTR

Destruye un `com::ptr`.

```cpp
~ptr();
```

### <a name="remarks"></a>Observaciones

En la destrucción, el `com::ptr` libera todas las referencias que posee a su objeto COM. Suponiendo que no hay otras referencias retenidas al objeto COM, se eliminará el objeto COM y se liberará su memoria.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto.  En la función `main`, se llamará a los dos destructores de los objetos `XmlDocument` cuando salgan del ámbito del bloque `try`, lo que provocará que se llame al destructor `com::ptr` subyacente, liberando todas las referencias propiedad del objeto COM.

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

## <a name="ptrattach"></a><a name="attach"></a>PTR:: Attach

Adjunta un objeto COM a un `com::ptr`.

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parámetros

*_right*<br/>
Puntero de interfaz COM que se va a adjuntar.

### <a name="exceptions"></a>Excepciones

Si el `com::ptr` ya posee una referencia a un objeto COM, `Attach` inicia <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Observaciones

Una llamada a `Attach` hace referencia al objeto COM, pero no libera la referencia del llamador a él.

Al pasar `NULL` a `Attach` no se realiza ninguna acción.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto. La función miembro `ReplaceDocument` llama primero a `Release` en cualquier objeto de propiedad anterior y, a continuación, llama a `Attach` para adjuntar un nuevo objeto de documento.

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

## <a name="ptrcreateinstance"></a><a name="createInstance"></a>PTR:: CreateInstance

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
Puntero a la interfaz IUnknown del objeto agregado (control IUnknown). Si no se especifica `pouter`, se utiliza `NULL`.

*cls_context*<br/>
Contexto en el que se ejecutará el código que administra el objeto recién creado. Los valores se toman de la enumeración `CLSCTX`. Si no se especifica `cls_context`, se usa el valor CLSCTX_ALL.

*rclsid*<br/>
`CLSID` asociados a los datos y el código que se utilizarán para crear el objeto.

### <a name="exceptions"></a>Excepciones

Si el `com::ptr` ya posee una referencia a un objeto COM, `CreateInstance` inicia <xref:System.InvalidOperationException>.

Esta función llama a `CoCreateInstance` y usa <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> para convertir cualquier `HRESULT` de error en una excepción adecuada.

### <a name="remarks"></a>Observaciones

`CreateInstance` usa `CoCreateInstance` para crear una nueva instancia del objeto especificado, identificada desde un ProgID o un CLSID. El `com::ptr` hace referencia al objeto recién creado y liberará automáticamente todas las referencias de propiedad en la destrucción.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto. Los constructores de clase usan dos formas diferentes de `CreateInstance` para crear el objeto de documento desde un ProgID o desde un CLSID más un CLSCTX.

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

## <a name="ptrdetach"></a><a name="detach"></a>PTR::D Etach

Proporciona la propiedad del objeto COM y devuelve un puntero al objeto.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto COM.

Si no hay ningún objeto propiedad, se devuelve NULL.

### <a name="exceptions"></a>Excepciones

Internamente, se llama a `QueryInterface` en el objeto COM de propiedad y se convierte cualquier `HRESULT` de error en una excepción mediante <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Observaciones

`Detach` primero agrega una referencia al objeto COM en nombre del llamador y, a continuación, libera todas las referencias propiedad del `com::ptr`.  El llamador debe liberar en última instancia el objeto devuelto para destruirlo.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto.  La función miembro `DetachDocument` llama `Detach` para proporcionar la propiedad del objeto COM y devolver un puntero al llamador.

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

## <a name="ptrgetinterface"></a><a name="getInterface"></a>PTR:: GetInterface

Devuelve un puntero al objeto COM de propiedad.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto COM de propiedad.

### <a name="exceptions"></a>Excepciones

Internamente, se llama a `QueryInterface` en el objeto COM de propiedad y se convierte cualquier `HRESULT` de error en una excepción mediante <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Observaciones

El `com::ptr` agrega una referencia al objeto COM en nombre del llamador y también mantiene su propia referencia en el objeto COM. En última instancia, el llamador debe liberar la referencia en el objeto devuelto o nunca se destruirá.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto. La función miembro `GetDocument` usa `GetInterface` para devolver un puntero al objeto COM.

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

## <a name="ptrqueryinterface"></a><a name="queryInterface"></a>PTR:: QueryInterface

Consulta el objeto COM de propiedad de una interfaz y asocia el resultado a otro `com::ptr`.

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Parámetros

*other*<br/>
`com::ptr` que obtendrá la interfaz.

### <a name="exceptions"></a>Excepciones

Internamente, se llama a `QueryInterface` en el objeto COM de propiedad y se convierte cualquier `HRESULT` de error en una excepción mediante <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Observaciones

Utilice este método para crear un contenedor COM para una interfaz diferente del objeto COM propiedad del contenedor actual. Este método llama a `QueryInterface` a través del objeto COM de propiedad para solicitar un puntero a una interfaz específica del objeto COM y asocia el puntero de interfaz devuelto al `com::ptr`pasado.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto. La función miembro `WriteTopLevelNode` usa `QueryInterface` para rellenar un `com::ptr` local con un `IXMLDOMNode` y, a continuación, pasa el `com::ptr` (mediante una referencia de seguimiento) a una función miembro privada que escribe las propiedades de texto y el nombre del nodo en la consola.

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

## <a name="ptrrelease"></a><a name="release"></a>PTR:: Release

Libera todas las referencias propiedad del objeto COM.

```cpp
void Release();
```

### <a name="remarks"></a>Observaciones

La llamada a esta función libera todas las referencias propiedad del objeto COM y establece el identificador interno del objeto COM en `nullptr`.  Si no existe ninguna otra referencia en el objeto COM, se destruirá.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto.  La función miembro `ReplaceDocument` usa `Release` para liberar cualquier objeto de documento anterior antes de adjuntar el nuevo documento.

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

## <a name="ptroperator-gt"></a><a name="operator-arrow"></a>PTR:: Operator-&gt;

Operador de acceso a miembros, que se usa para llamar a métodos en el objeto COM de propiedad.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Valor devuelto

`smart_com_ptr` al objeto COM.

### <a name="exceptions"></a>Excepciones

Internamente, se llama a `QueryInterface` en el objeto COM de propiedad y se convierte cualquier `HRESULT` de error en una excepción mediante <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Observaciones

Este operador le permite llamar a métodos del objeto COM de propiedad. Devuelve un `smart_com_ptr` temporal que controla automáticamente sus propios `AddRef` y `Release`.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto. La función `WriteDocument` utiliza `operator->` para llamar al miembro `get_firstChild` del objeto de documento.

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

## <a name="ptroperator"></a><a name="operator-assign"></a>PTR:: Operator =

Adjunta un objeto COM a un `com::ptr`.

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parámetros

*_right*<br/>
Puntero de interfaz COM que se va a adjuntar.

### <a name="return-value"></a>Valor devuelto

Referencia de seguimiento en el `com::ptr`.

### <a name="exceptions"></a>Excepciones

Si el `com::ptr` ya posee una referencia a un objeto COM, `operator=` inicia <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Observaciones

La asignación de un objeto COM a un `com::ptr` hace referencia al objeto COM, pero no libera la referencia del llamador a él.

Este operador tiene el mismo efecto que `Attach`.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto.  La función miembro `ReplaceDocument` llama primero a `Release` en cualquier objeto de propiedad anterior y, a continuación, usa `operator=` para adjuntar un nuevo objeto de documento.

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

## <a name="ptroperator-bool"></a><a name="operator-bool"></a>PTR:: Operator bool

Operador para usar `com::ptr` en una expresión condicional.

```cpp
operator bool();
```

### <a name="return-value"></a>Valor devuelto

`true` si el objeto COM de propiedad es válido; de lo contrario `false`.

### <a name="remarks"></a>Observaciones

El objeto COM de propiedad es válido si no se `nullptr`.

Este operador convierte en `_detail_class::_safe_bool` que es más seguro que `bool` porque no se puede convertir en un tipo entero.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto. La función miembro `CreateInstance` usa `operator bool` después de crear el nuevo objeto de documento para determinar si es válido y escribe en la consola si es.

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

## <a name="ptroperator"></a><a name="operator-logical-not"></a>PTR:: Operator!

Para determinar si el objeto COM de propiedad no es válido.

```cpp
bool operator!();
```

### <a name="return-value"></a>Valor devuelto

`true` si el objeto COM de propiedad no es válido; de lo contrario `false`.

### <a name="remarks"></a>Observaciones

El objeto COM de propiedad es válido si no se `nullptr`.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa una clase de CLR que utiliza un `com::ptr` para encapsular su miembro privado `IXMLDOMDocument` objeto.  La función miembro `CreateInstance` usa `operator!` para determinar si un objeto de documento ya es propiedad de y solo crea una nueva instancia si el objeto no es válido.

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
