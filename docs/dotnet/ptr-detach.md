---
title: "ptr::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ptr.Detach"
  - "msclr.com.ptr.Detach"
  - "ptr::Detach"
  - "msclr::com::ptr::Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr::Detach"
ms.assetid: 23370c8a-8f79-4880-9fa1-46e110c1a92c
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# ptr::Detach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Abandona la propiedad del objeto COM, devolviendo un puntero al objeto.  
  
## Sintaxis  
  
```  
_interface_type * Detach();  
```  
  
## Valor devuelto  
 El puntero al objeto COM.  
  
 Si no se posee ningún objeto, se devuelve NULL.  
  
## Excepciones  
 Internamente, `QueryInterface` se llama en el objeto COM en propiedad y los errores `HRESULT` se convierte en una excepción por <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.  
  
## Comentarios  
 `Detach` primero agrega una referencia al objeto COM en nombre del llamador y luego las versiones que todas las referencias poseyeron por `com::ptr`.  El llamador debe liberar finalmente el objeto devuelto para destruirlo.  
  
## Ejemplo  
 Este ejemplo implementa una clase CLR que utilice `com::ptr` para ajustar su objeto de `IXMLDOMDocument` miembro privado.  Las llamadas de función `Detach` miembro de `DetachDocument` para abandonar la propiedad del objeto COM y devolver un puntero al llamador.  
  
```  
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
  
## Requisitos  
 **Archivo de encabezado** \<msclr\\com\\ptr.h\>  
  
 msclr::com de**Namespace**  
  
## Vea también  
 [ptr \(Miembros\)](../dotnet/ptr-members.md)   
 [ptr::Release](../dotnet/ptr-release.md)   
 [ptr::Attach](../dotnet/ptr-attach.md)