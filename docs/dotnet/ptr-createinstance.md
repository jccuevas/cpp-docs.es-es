---
title: "ptr::CreateInstance | Microsoft Docs"
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
  - "ptr.CreateInstance"
  - "msclr::com::ptr::CreateInstance"
  - "msclr.com.ptr.CreateInstance"
  - "ptr::CreateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr::CreateInstance"
ms.assetid: 9e8e4c4c-1651-4839-8829-5857d74470fe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ptr::CreateInstance
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea una instancia de un objeto COM dentro de `com::ptr`.  
  
## Sintaxis  
  
```  
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
  
#### Parámetros  
 `progid`  
 una cadena de `ProgID` .  
  
 `pouter`  
 Puntero a la interfaz IUnknown del objeto global \(el IUnknown que controla\).  Si `pouter` no se especifica, se utiliza `NULL` .  
  
 `cls_context`  
 Contexto en el que el código que administra el objeto recién creado se ejecutará.  Los valores se toman de la enumeración de `CLSCTX` .  Si `cls_context` no se especifica, se utiliza el valor CLSCTX\_ALL.  
  
 `rclsid`  
 `CLSID` asociada a los datos y el código que se usarán para crear el objeto.  
  
## Excepciones  
 Si `com::ptr` ya posee una referencia a un objeto COM, `CreateInstance` produce <xref:System.InvalidOperationException>.  
  
 Este las llamadas de función `CoCreateInstance` y utilizan <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> para convertir cualquier error `HRESULT` a una excepción adecuada.  
  
## Comentarios  
 `CreateInstance` utiliza `CoCreateInstance` para crear una nueva instancia del objeto especificado, identificada de ProgID o de CLSID.  `com::ptr` hace referencia al objeto recién creado y automáticamente libera todas las referencias que pertenecen a la destrucción.  
  
## Ejemplo  
 Este ejemplo implementa una clase CLR que utilice `com::ptr` para ajustar su objeto de `IXMLDOMDocument` miembro privado.  Los constructores de clase usan dos formas de `CreateInstance` para crear el objeto document de ProgID o de CLSID más un CLSCTX.  
  
```  
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
  
## Requisitos  
 **Archivo de encabezado** \<msclr\\com\\ptr.h\>  
  
 msclr::com de**Namespace**  
  
## Vea también  
 [ptr \(Miembros\)](../dotnet/ptr-members.md)