---
title: "ptr::ptr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ptr::ptr"
  - "ptr.ptr"
  - "msclr.com.ptr.ptr"
  - "msclr::com::ptr::ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr::ptr"
ms.assetid: 4f5883b4-7c0a-46c6-aa9f-4e49eed463eb
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ptr::ptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye `com::ptr` para ajustar un objeto COM.  
  
## Sintaxis  
  
```  
ptr();  
ptr(  
   _interface_type * p  
);  
```  
  
#### Parámetros  
 `P`  
 Puntero a interfaz COM.  
  
## Comentarios  
 El constructor de ninguno\- argumento asigna `nullptr` el controlador de objeto subyacente.  Las llamadas subsiguientes a `com::ptr` se validan el objeto interno y producirán errores silenciosamente hasta que un objeto se crea o se adjunte realmente.  
  
 El constructor de uno\- argumento agrega una referencia al objeto COM pero no libera la referencia del llamador, por lo que el llamador debe llamar a `Release` en el objeto COM para dar true para buscar el control.  Cuando se llama a `com::ptr` destructor automáticamente libera las referencias en el objeto COM.  
  
 Pasar `NULL` a este constructor es igual que llamar a la versión de ninguno\- argumento.  
  
## Ejemplo  
 Este ejemplo implementa una clase CLR que utilice `com::ptr` para ajustar su objeto de `IXMLDOMDocument` miembro privado.  Muestra el uso de las dos versiones del constructor.  
  
```  
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
  
## Requisitos  
 **Archivo de encabezado** \<msclr\\com\\ptr.h\>  
  
 msclr::com de**Namespace**  
  
## Vea también  
 [ptr \(Miembros\)](../dotnet/ptr-members.md)   
 [ptr::CreateInstance](../dotnet/ptr-createinstance.md)   
 [ptr::~ptr](../dotnet/ptr-tilde-ptr.md)