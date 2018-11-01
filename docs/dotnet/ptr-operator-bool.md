---
title: ptr::operator bool
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ptr::operator bool
- ptr.operator bool
- operator bool
- msclr::com::ptr::operator bool
- msclr.com.ptr.operator bool
helpviewer_keywords:
- ptr::operator bool
ms.assetid: 31123377-6ecd-4cef-9b75-3db3996fbcd1
ms.openlocfilehash: 185db15a62cc676c771f60a54c583e19e28e95be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509674"
---
# <a name="ptroperator-bool"></a>ptr::operator bool

Operador para el uso de `com::ptr` en una expresión condicional.

## <a name="syntax"></a>Sintaxis

```
operator bool();
```

## <a name="return-value"></a>Valor devuelto

**True** si es válido; el objeto COM que se poseen **false** en caso contrario.

## <a name="remarks"></a>Comentarios

Es válido si no es el objeto COM que se poseen `nullptr`.

Este operador convierte realmente en `_detail_class::_safe_bool` que es más seguro que `bool` porque no se puede convertir a un tipo entero.

## <a name="example"></a>Ejemplo

En este ejemplo implementa una clase CLR que utiliza un `com::ptr` para ajustar su miembro privado `IXMLDOMDocument` objeto. El `CreateInstance` usa la función miembro `operator bool` después de crear el nuevo objeto de documento para determinar si es válido y escribe en la consola si lo es.

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

```Output
DOM Document created.
```

## <a name="requirements"></a>Requisitos

**Archivo de encabezado** \<msclr\com\ptr.h >

**Namespace** msclr::com

## <a name="see-also"></a>Vea también

[ptr (Miembros)](../dotnet/ptr-members.md)<br/>
[ptr::operator!](../dotnet/ptr-operator-logical-not.md)