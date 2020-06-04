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
ms.openlocfilehash: e494285f33cf282d7b7515aac374ec86ef3036b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372484"
---
# <a name="comptr-class"></a>com::ptr (Clase)

Un contenedor para un objeto COM que se puede usar como miembro de una clase CLR.  El contenedor también automatiza la administración de la duración del objeto COM, liberando todas las referencias de propiedad en el objeto cuando se llama a su destructor. Análogo a [la clase CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Sintaxis

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Parámetros

*_interface_type*<br/>
Interfaz COM.

## <a name="remarks"></a>Observaciones

A `com::ptr` también se puede utilizar como variable de función local para simplificar varias tareas COM y automatizar la administración de por vida.

A `com::ptr` no se puede utilizar directamente como un parámetro de función; utilice un operador de [referencia tracking](../extensions/tracking-reference-operator-cpp-component-extensions.md) o un operador Handle to [object (en su lugar).](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

A `com::ptr` no se puede devolver directamente desde una función; utilizar un mango en su lugar.

## <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado.  Llamar a los métodos públicos de `IXMLDOMDocument` la clase da como resultado llamadas al objeto contenido.  El ejemplo crea una instancia de un documento XML, la rellena con un XML simple y realiza un paseo simplificado de los nodos del árbol de documentos analizados para imprimir el XML en la consola.

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

|Nombre|Descripción|
|---------|-----------|
|[ptr::ptr](#ptr)|Construye `com::ptr` a para ajustar un objeto COM.|
|[ptr::-ptr](#tilde-ptr)|Destruye un `com::ptr`archivo .|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|---------|-----------|
|[ptr::Attach](#attach)|Asocia un objeto COM `com::ptr`a un archivo .|
|[ptr::CreateInstance](#createInstance)|Crea una instancia de un `com::ptr`objeto COM dentro de un archivo .|
|[ptr::Detach](#detach)|Renuncia a la propiedad del objeto COM, devolviendo un puntero al objeto.|
|[ptr::GetInterface](#getInterface)|Crea una instancia de un `com::ptr`objeto COM dentro de un archivo .|
|[ptr::QueryInterface](#queryInterface)|Consulta el objeto COM de propiedad de una `com::ptr`interfaz y adjunta el resultado a otra .|
|[ptr::Release](#release)|Libera todas las referencias propiedad en el objeto COM.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|---------|-----------|
|[ptr::operador-&gt;](#operator-arrow)|Operador de acceso de miembro, utilizado para llamar a métodos en el objeto COM de propiedad.|
|[ptr::operador ?](#operator-assign)|Asocia un objeto COM `com::ptr`a un archivo .|
|[ptr::operator&nbsp;bool](#operator-bool)|Operador para `com::ptr` usar en una expresión condicional.|
|[ptr::operator!](#operator-logical-not)|Operador para determinar si el objeto COM de propiedad no es válido.|

## <a name="requirements"></a>Requisitos

**Archivo de encabezado** \<msclr-com-ptr.h>

**Espacio de nombres** msclr::com

## <a name="ptrptr"></a><a name="ptr"></a>ptr::ptr

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

El constructor sin `nullptr` argumento se asigna al identificador de objeto subyacente. Las llamadas `com::ptr` futuras a la validarán el objeto interno y se produciráun un error en silencio hasta que se cree o se adjunta un objeto.

El constructor de un argumento agrega una referencia al objeto COM pero no libera la `Release` referencia del llamador, por lo que el llamador debe llamar al objeto COM para renunciar realmente al control. Cuando `com::ptr`se llama al destructor 's, liberará automáticamente sus referencias en el objeto COM.

Pasar `NULL` a este constructor es lo mismo que llamar a la versión sin argumento.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado. Muestra el uso de ambas versiones del constructor.

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

## <a name="ptrptr"></a><a name="tilde-ptr"></a>ptr::-ptr

Destruye un `com::ptr`archivo .

```cpp
~ptr();
```

### <a name="remarks"></a>Observaciones

En la `com::ptr` destrucción, las liberaciones de todas las referencias que posee a su objeto COM. Suponiendo que no hay otras referencias mantenidas al objeto COM, se eliminará el objeto COM y se liberará su memoria.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado.  En `main` la función, se llamará a los destructores de los dos `XmlDocument` objetos cuando salgan del ámbito del `try` bloque, lo que dará como resultado el nombre del destructor subyacente, `com::ptr` liberando todas las referencias de propiedad al objeto COM.

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

## <a name="ptrattach"></a><a name="attach"></a>ptr::Adjuntar

Asocia un objeto COM `com::ptr`a un archivo .

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parámetros

*_right*<br/>
El puntero de interfaz COM que se va a adjuntar.

### <a name="exceptions"></a>Excepciones

Si `com::ptr` el ya posee una referencia `Attach` a <xref:System.InvalidOperationException>un objeto COM, produce .

### <a name="remarks"></a>Observaciones

Una llamada `Attach` a hace referencia al objeto COM pero no libera la referencia del autor de la llamada a él.

Pasar `NULL` `Attach` a resultados en ninguna acción que se está realizando.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado. La `ReplaceDocument` función `Release` miembro primero llama a `Attach` cualquier objeto de propiedad anterior y, a continuación, llama para adjuntar un nuevo objeto de documento.

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

## <a name="ptrcreateinstance"></a><a name="createInstance"></a>ptr::CreateInstance

Crea una instancia de un `com::ptr`objeto COM dentro de un archivo .

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

*Progid*<br/>
Cadena de `ProgID`.

*pouter*<br/>
Puntero a la interfaz IUnknown del objeto agregado (el control IUnknown). Si `pouter` no se especifica, `NULL` se usa.

*cls_context*<br/>
Contexto en el que se ejecutará el código que administra el objeto recién creado. Los valores se `CLSCTX` toman de la enumeración. Si `cls_context` no se especifica, se utiliza el valor CLSCTX_ALL.

*rclsid*<br/>
`CLSID`asociados con los datos y el código que se usará para crear el objeto.

### <a name="exceptions"></a>Excepciones

Si `com::ptr` el ya posee una referencia `CreateInstance` a <xref:System.InvalidOperationException>un objeto COM, produce .

Esta función `CoCreateInstance` <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> llama y `HRESULT` utiliza para convertir cualquier error en una excepción adecuada.

### <a name="remarks"></a>Observaciones

`CreateInstance`se `CoCreateInstance` utiliza para crear una nueva instancia del objeto especificado, identificada a partir de un ProgID o un CLSID. Las `com::ptr` referencias al objeto recién creado y liberarán automáticamente todas las referencias de propiedad tras la destrucción.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado. Los constructores de clase `CreateInstance` utilizan dos formas diferentes de crear el objeto de documento a partir de un ProgID o de un CLSID más un CLSCTX.

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

## <a name="ptrdetach"></a><a name="detach"></a>ptr::Detach

Renuncia a la propiedad del objeto COM, devolviendo un puntero al objeto.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Valor devuelto

El puntero al objeto COM.

Si no se pertenece a ningún objeto, se devuelve NULL.

### <a name="exceptions"></a>Excepciones

Internamente, `QueryInterface` se llama en el `HRESULT` objeto COM de <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>propiedad y cualquier error se convierte en una excepción por .

### <a name="remarks"></a>Observaciones

`Detach`primero agrega una referencia al objeto COM en nombre del autor `com::ptr`de la llamada y, a continuación, libera todas las referencias propiedad de la .  En última instancia, el autor de la llamada debe liberar el objeto devuelto para destruirlo.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado.  La `DetachDocument` función `Detach` miembro llama para renunciar a la propiedad del objeto COM y devolver un puntero al llamador.

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

## <a name="ptrgetinterface"></a><a name="getInterface"></a>ptr::GetInterface

Devuelve un puntero al objeto COM de propiedad.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto COM de propiedad.

### <a name="exceptions"></a>Excepciones

Internamente, `QueryInterface` se llama en el `HRESULT` objeto COM de <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>propiedad y cualquier error se convierte en una excepción por .

### <a name="remarks"></a>Observaciones

El `com::ptr` agrega una referencia al objeto COM en nombre del autor de la llamada y también mantiene su propia referencia en el objeto COM. En última instancia, el autor de la llamada debe liberar la referencia en el objeto devuelto o nunca se destruirá.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado. La `GetDocument` función `GetInterface` miembro se utiliza para devolver un puntero al objeto COM.

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

## <a name="ptrqueryinterface"></a><a name="queryInterface"></a>ptr::QueryInterface

Consulta el objeto COM de propiedad de una `com::ptr`interfaz y adjunta el resultado a otra .

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
El `com::ptr` que obtendrá la interfaz.

### <a name="exceptions"></a>Excepciones

Internamente, `QueryInterface` se llama en el `HRESULT` objeto COM de <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>propiedad y cualquier error se convierte en una excepción por .

### <a name="remarks"></a>Observaciones

Utilice este método para crear un contenedor COM para una interfaz diferente del objeto COM propiedad del contenedor actual. Este método `QueryInterface` llama a través del objeto COM de propiedad para solicitar un puntero a una `com::ptr`interfaz específica del objeto COM y adjunta el puntero de interfaz devuelto al pasado .

### <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado. La `WriteTopLevelNode` función `QueryInterface` miembro se `com::ptr` utiliza `IXMLDOMNode` para rellenar `com::ptr` un local con un y, a continuación, pasa el (por referencia de seguimiento) a una función miembro privada que escribe el nombre del nodo y las propiedades de texto en la consola.

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

## <a name="ptrrelease"></a><a name="release"></a>ptr::Liberar

Libera todas las referencias propiedad en el objeto COM.

```cpp
void Release();
```

### <a name="remarks"></a>Observaciones

Al llamar a esta función se liberan todas las referencias `nullptr`de propiedad en el objeto COM y se establece el identificador interno en el objeto COM en .  Si no existen otras referencias en el objeto COM, se destruirá.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado.  La `ReplaceDocument` función `Release` miembro se utiliza para liberar cualquier objeto de documento anterior antes de adjuntar el nuevo documento.

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

## <a name="ptroperator-gt"></a><a name="operator-arrow"></a>ptr::operador-&gt;

Operador de acceso de miembro, utilizado para llamar a métodos en el objeto COM de propiedad.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Valor devuelto

A `smart_com_ptr` para el objeto COM.

### <a name="exceptions"></a>Excepciones

Internamente, `QueryInterface` se llama en el `HRESULT` objeto COM de <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>propiedad y cualquier error se convierte en una excepción por .

### <a name="remarks"></a>Observaciones

Este operador permite llamar a métodos del objeto COM de propiedad. Devuelve un `smart_com_ptr` temporal que controla automáticamente su propio `AddRef` y `Release`.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado. La `WriteDocument` función se utiliza `operator->` para llamar al `get_firstChild` miembro del objeto de documento.

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

## <a name="ptroperator"></a><a name="operator-assign"></a>ptr::operador ?

Asocia un objeto COM `com::ptr`a un archivo .

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parámetros

*_right*<br/>
El puntero de interfaz COM que se va a adjuntar.

### <a name="return-value"></a>Valor devuelto

Una referencia de `com::ptr`seguimiento en el archivo .

### <a name="exceptions"></a>Excepciones

Si `com::ptr` el ya posee una referencia `operator=` a <xref:System.InvalidOperationException>un objeto COM, produce .

### <a name="remarks"></a>Observaciones

Asignar un objeto `com::ptr` COM a un objeto COM, pero no libera la referencia del autor de la llamada a él.

Este operador tiene el `Attach`mismo efecto que .

### <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado.  La `ReplaceDocument` función `Release` miembro primero llama a `operator=` cualquier objeto de propiedad anterior y, a continuación, se utiliza para adjuntar un nuevo objeto de documento.

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

## <a name="ptroperator-bool"></a><a name="operator-bool"></a>ptr::operator bool

Operador para `com::ptr` usar en una expresión condicional.

```cpp
operator bool();
```

### <a name="return-value"></a>Valor devuelto

`true`si el objeto COM de propiedad es válido; `false` de lo contrario.

### <a name="remarks"></a>Observaciones

El objeto COM de propiedad es `nullptr`válido si no lo es.

Este operador se `_detail_class::_safe_bool` convierte a `bool` que es más seguro que porque no se puede convertir en un tipo entero.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado. La `CreateInstance` función `operator bool` miembro se utiliza después de crear el nuevo objeto de documento para determinar si es válido y escribe en la consola si lo es.

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

## <a name="ptroperator"></a><a name="operator-logical-not"></a>ptr::operador!

Operador para determinar si el objeto COM de propiedad no es válido.

```cpp
bool operator!();
```

### <a name="return-value"></a>Valor devuelto

`true`si el objeto COM propiedad no es válido; `false` de lo contrario.

### <a name="remarks"></a>Observaciones

El objeto COM de propiedad es `nullptr`válido si no lo es.

### <a name="example"></a>Ejemplo

En este ejemplo se implementa `com::ptr` una clase CLR `IXMLDOMDocument` que usa a para ajustar su objeto miembro privado.  La `CreateInstance` función `operator!` miembro se utiliza para determinar si un objeto de documento ya es propiedad y solo crea una nueva instancia si el objeto no es válido.

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
