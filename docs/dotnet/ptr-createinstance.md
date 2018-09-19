---
title: PTR::CreateInstance | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr.CreateInstance
- msclr::com::ptr::CreateInstance
- msclr.com.ptr.CreateInstance
- ptr::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- ptr::CreateInstance
ms.assetid: 9e8e4c4c-1651-4839-8829-5857d74470fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8f03a4f0cfb2b231e9a453009155308f7bf407db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112218"
---
# <a name="ptrcreateinstance"></a>ptr::CreateInstance
Crea una instancia de un objeto COM dentro de un `com::ptr`.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
*progid*<br/>
Cadena de `ProgID`.  
  
*pouter*<br/>
Puntero a interfaz de IUnknown del objeto agregado (IUnknown de control). Si `pouter` no se especifica, `NULL` se utiliza.  
  
*cls_context*<br/>
Contexto en que se ejecutará el código que administra el objeto recién creado. Los valores se toman de la `CLSCTX` enumeración. Si `cls_context` no se especifica, el valor se usa CLSCTX_ALL.  
  
*rclsid*<br/>
`CLSID` asociado con los datos y el código que se usará para crear el objeto.  
  
## <a name="exceptions"></a>Excepciones  
 Si el `com::ptr` ya posee una referencia a un objeto COM, `CreateInstance` produce <xref:System.InvalidOperationException>.  
  
 Esta función llama a `CoCreateInstance` y usa <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> para convertir cualquier error `HRESULT` a una excepción adecuada.  
  
## <a name="remarks"></a>Comentarios  
 `CreateInstance` usa `CoCreateInstance` para crear una nueva instancia del objeto especificado, identificado desde un ProgID o CLSID. El `com::ptr` hace referencia al objeto recién creado y liberará automáticamente las referencias de todos los que se poseen tras la destrucción.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto. Los constructores de clase utilizan dos formas diferentes de `CreateInstance` para crear el objeto de documento desde un ProgID o CLSID además un CLSCTX.  
  
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
  
## <a name="requirements"></a>Requisitos  
 **Archivo de encabezado** \<msclr\com\ptr.h >  
  
 **Namespace** msclr::com  
  
## <a name="see-also"></a>Vea también  
 [ptr (Miembros)](../dotnet/ptr-members.md)