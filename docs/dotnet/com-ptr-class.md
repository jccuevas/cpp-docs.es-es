---
title: "com::ptr (Clase) | Microsoft Docs"
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
  - "com::ptr"
  - "msclr::com::ptr"
  - "msclr.com.ptr"
  - "com.ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr (clase)"
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# com::ptr (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un contenedor para un objeto COM que se puede utilizar como miembro de una clase CLR.  El contenedor también automatiza la administración de la duración del objeto COM, liberando todas las referencias que son propiedad del objeto cuando se llama al destructor.  Análogo a [CComPtr Class](../atl/reference/ccomptr-class.md).  
  
## Sintaxis  
  
```  
template<class _interface_type>  
ref class ptr;  
```  
  
#### Parámetros  
 `_interface_type`  
 Interfaz COM.  
  
## Comentarios  
 `com::ptr` también se puede utilizar como una variable de la función local para simplificar tareas diferentes COM y automatizar la administración de la duración.  
  
 `com::ptr` no se puede utilizar directamente como parámetro de la función; utilice [Operador de referencia de seguimiento](../windows/tracking-reference-operator-cpp-component-extensions.md) o [Identificador a un operador de objeto \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md) en su lugar.  
  
 `com::ptr` no se puede devolver directamente de una función; utilice un identificador en su lugar.  
  
## Ejemplo  
 Este ejemplo implementa una clase CLR que utilice `com::ptr` para ajustar su objeto de `IXMLDOMDocument` miembro privado.  Llamar a los métodos públicos de la clase da lugar a llamadas al objeto contenido de `IXMLDOMDocument` .  En el ejemplo se crea una instancia de un documento XML, la rellena con algún XML simple, y realiza un recorrido simplificado de los nodos del árbol analizado del documento para imprimir XML en la consola.  
  
```  
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
  
  **\<wordpersnickety\>\<3\/palabra\>**   
## Requisitos  
 **Archivo de encabezado** \<msclr\\com\\ptr.h\>  
  
 msclr::com de**Namespace**  
  
## Vea también  
 [Biblioteca de compatibilidad de C\+\+](../dotnet/cpp-support-library.md)   
 [ptr \(Miembros\)](../dotnet/ptr-members.md)