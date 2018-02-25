---
title: Admitir el subprocesamiento libre en un proveedor | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5cd5ce6b852b490334cbc8d49c6e967efffb3a6e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="supporting-free-threading-in-your-provider"></a>Admitir el subprocesamiento libre en un proveedor
Todas las clases de proveedor de OLE DB son seguras para subprocesos y entradas del registro se establecen en consecuencia. Es una buena idea para admitir el subprocesamiento libre para ayudar a proporcionar un alto nivel de rendimiento en situaciones multiusuario. Para ayudar a mantener su proveedor de subprocesos, debe comprobar que el código está bloqueado correctamente. Cada vez que intenta escribir o almacena los datos, debe bloquear el acceso con secciones críticas.  
  
 Cada objeto de plantilla de proveedor OLE DB tiene su propia sección crítica. Para facilitar el bloqueo, cada clase nueva que cree debe ser una clase de plantilla que toma la clase primaria nombre como un argumento.  
  
 En el ejemplo siguiente se muestra cómo bloquear el código:  
  
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
  
 Para obtener más información acerca de cómo proteger las secciones críticas con `Lock` y `Unlock`, consulte [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
 También debe comprobar que todos los métodos de invalidación (como `Execute`) son seguras para subprocesos.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)