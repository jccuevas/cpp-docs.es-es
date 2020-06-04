---
title: Admitir el subprocesamiento libre en un proveedor
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
ms.openlocfilehash: 50e05b70a782dd343031443540790697e980c994
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209560"
---
# <a name="supporting-free-threading-in-your-provider"></a>Admitir el subprocesamiento libre en un proveedor

Todas las clases de proveedor de OLE DB son seguras para subprocesos y las entradas del registro se establecen en consecuencia. Es una buena idea admitir el subprocesamiento libre para ayudar a proporcionar un alto nivel de rendimiento en situaciones de varios usuarios. Para ayudar a mantener la seguridad para subprocesos del proveedor, debe comprobar que el código está bloqueado correctamente. Siempre que escriba o almacene datos, debe bloquear el acceso con secciones críticas.

Cada objeto de plantilla de proveedor de OLE DB tiene su propia sección crítica. Para facilitar el bloqueo, cada nueva clase que cree debe ser una clase de plantilla que tome el nombre de la clase primaria como argumento.

En el ejemplo siguiente se muestra cómo bloquear el código:

```cpp
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

Para obtener más información sobre cómo proteger las secciones críticas con `Lock` y `Unlock`, vea [multithreading: uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

Compruebe que los métodos invalidados (como `Execute`) son seguros para subprocesos.

## <a name="see-also"></a>Consulte también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
