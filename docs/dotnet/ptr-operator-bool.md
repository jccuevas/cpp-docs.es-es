---
title: "ptr::operator bool | Microsoft Docs"
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
  - "ptr::operator bool"
  - "ptr.operator bool"
  - "operator bool"
  - "msclr::com::ptr::operator bool"
  - "msclr.com.ptr.operator bool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr::operator bool"
ms.assetid: 31123377-6ecd-4cef-9b75-3db3996fbcd1
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ptr::operator bool
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Operador para utilizar `com::ptr` en una expresión condicional.  
  
## Sintaxis  
  
```  
operator bool();  
```  
  
## Valor devuelto  
 `true` si el objeto COM propiedad es válido; `false` de otra manera.  
  
## Comentarios  
 El objeto COM propiedad es válido si no es `nullptr`.  
  
 Este operador convierte realmente a `_detail_class::_safe_bool` que es más seguro que `bool` porque no puede convertirse a un tipo entero.  
  
## Ejemplo  
 Este ejemplo implementa una clase CLR que utilice `com::ptr` para ajustar su objeto de `IXMLDOMDocument` miembro privado.  La función miembro de `CreateInstance` utiliza `operator bool` después de crear el nuevo objeto document para determinar si es válida y escribe en la consola si es.  
  
```  
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
  
  **Documento DOM creado.**   
## Requisitos  
 **Archivo de encabezado** \<msclr\\com\\ptr.h\>  
  
 msclr::com de**Namespace**  
  
## Vea también  
 [ptr \(Miembros\)](../dotnet/ptr-members.md)   
 [ptr::operator\!](../dotnet/ptr-operator-logical-not.md)