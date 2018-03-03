---
title: PTR::Attach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::com::ptr::Attach
- ptr::Attach
- ptr.Attach
- msclr.com.ptr.Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method
ms.assetid: 81d930de-cb2a-4c30-9bd6-94d65942c47a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d8e3a107bef12ca7f1bcd89098d35ed6a124775f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ptrattach"></a>ptr::Attach
Asocia un objeto COM para un `com::ptr`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void Attach(  
   _interface_type * _right  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `_right`  
 El puntero de interfaz COM para adjuntar.  
  
## <a name="exceptions"></a>Excepciones  
 Si el `com::ptr` ya posee una referencia a un objeto COM, `Attach` produce <xref:System.InvalidOperationException>.  
  
## <a name="remarks"></a>Comentarios  
 Una llamada a `Attach` hace referencia al objeto COM pero no libera la referencia del llamador.  
  
 Pasar `NULL` a `Attach` da como resultado que se va a realizar ninguna acción.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto. El `ReplaceDocument` llama primero a la función de miembro `Release` en cualquier previamente propiedad de objeto y, a continuación, llama `Attach` para anexar un nuevo objeto de documento.  
  
```  
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
  
## <a name="requirements"></a>Requisitos  
 **Archivo de encabezado** \<msclr\com\ptr.h >  
  
 **Namespace** msclr::com  
  
## <a name="see-also"></a>Vea también  
 [PTR (miembros)](../dotnet/ptr-members.md)   
 [PTR::operator =](../dotnet/ptr-operator-assign.md)   
 [ptr::Release](../dotnet/ptr-release.md)