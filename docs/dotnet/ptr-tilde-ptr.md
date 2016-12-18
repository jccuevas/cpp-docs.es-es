---
title: "ptr::~ptr | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr.com.ptr.~ptr"
  - "ptr.~ptr"
  - "msclr::com.ptr::~ptr"
  - "~ptr"
  - "ptr::~ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr::~ptr"
ms.assetid: 5f644aa5-fe66-4992-a5f8-13ec1292c949
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ptr::~ptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Destructs `com::ptr`.  
  
## Sintaxis  
  
```  
~ptr();  
```  
  
## Comentarios  
 En la destrucción, libera de `com::ptr` todas las referencias que pertenece al objeto COM.  Suponiendo que no hay ninguna otras referencias contenía el objeto COM, el objeto COM se eliminará y su memoria se liberará.  
  
## Ejemplo  
 Este ejemplo implementa una clase CLR que utilice `com::ptr` para ajustar su objeto de `IXMLDOMDocument` miembro privado.  En función de `main` , destructores los dos de los objetos de `XmlDocument` se llamará cuando salen del ámbito del bloque de `try` , por lo que `com::ptr` subyacente destructor llamado, liberando todas las referencias que pertenecen al objeto COM.  
  
```  
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
  
## Requisitos  
 **Archivo de encabezado** \<msclr\\com\\ptr.h\>  
  
 msclr::com de**Namespace**  
  
## Vea también  
 [ptr \(Miembros\)](../dotnet/ptr-members.md)   
 [ptr::ptr](../dotnet/ptr-ptr.md)   
 [ptr::CreateInstance](../dotnet/ptr-createinstance.md)