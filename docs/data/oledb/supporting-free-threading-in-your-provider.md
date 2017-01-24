---
title: "Admitir el subprocesamiento libre en un proveedor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "proveedores OLE DB, con subprocesamiento múltiple"
  - "subprocesamiento [C++], proveedores"
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Admitir el subprocesamiento libre en un proveedor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Todas las clases de proveedor OLE DB son seguras para subprocesos y se establecerán las entradas del Registro de acuerdo con esto.  Es recomendable admitir el subprocesamiento libre para ayudar a proporcionar un alto nivel de rendimiento en situaciones multiusuario.  Para ayudar a mantener la seguridad de subprocesos del proveedor, debe comprobar que el código está correctamente bloqueado.  Siempre que escriba o almacene datos debe bloquear el acceso con secciones críticas.  
  
 Cada objeto de plantilla del proveedor OLE DB tiene su propia sección crítica.  Para facilitar el bloqueo, cada clase nueva que cree deberá ser una plantilla que utilice el nombre de la clase primaria como argumento.  
  
 En el ejemplo siguiente, se muestra cómo bloquear el código:  
  
```  
template <class T>  
class CMyObject<T> : public...  
  
HRESULT MyObject::MyMethod(void)  
{  
   T* pT = (T*)this;      // this gets the parent class   
  
// You don't need to do anything if you are only reading information  
  
// If you want to write information, do the following:  
   pT->Lock();         // engages critical section in the object  
   ...;                // write whatever information you wish  
   pT->Unlock();       // disengages the critical section  
}  
```  
  
 Para obtener información sobre cómo proteger las secciones críticas mediante `Lock` y `Unlock`, vea [Multithreading: Uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
 También debe comprobar que los métodos que reemplace \(como `Execute`\) sean seguros para subprocesos.  
  
## Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)