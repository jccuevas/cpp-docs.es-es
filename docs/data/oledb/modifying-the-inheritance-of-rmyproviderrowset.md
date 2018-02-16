---
title: Modificar la herencia de RMyProviderRowset | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 89f67a5be8ba68ef75a2c13fdbfb8c812812fcb3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="modifying-the-inheritance-of-rmyproviderrowset"></a>Modificar la herencia de RMyProviderRowset
Para agregar el `IRowsetLocate` de la interfaz para el ejemplo de proveedor sencillo de sólo lectura, modifique la herencia de **RMyProviderRowset**. Inicialmente, **RMyProviderRowset** hereda de `CRowsetImpl`. Debe modificar que herede de **CRowsetBaseImpl**.  
  
 Para ello, cree una nueva clase, `CMyRowsetImpl`, en MyProviderRS.h:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>  
{  
...  
};  
```  
  
 Ahora, edite el mapa de interfaz COM: MyProviderRS.h para ser como sigue:  
  
```  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 Esto crea un mapa de interfaz COM que indica a `CMyRowsetImpl` para llamar a **QueryInterface** tanto para el `IRowset` y `IRowsetLocate` interfaces. Para obtener toda la implementación para el conjunto de filas de otra clases, los vínculos del mapa la `CMyRowsetImpl` clase de nuevo a la **CRowsetBaseImpl** clase definida por las plantillas OLE DB; el mapa utiliza la macro COM_INTERFACE_ENTRY_CHAIN, que indica a Plantillas OLE DB para examinar el modelo COM se asignan en **CRowsetBaseImpl** en respuesta a un `QueryInterface` llamar.  
  
 Por último, vincule `RAgentRowset` a `CMyRowsetBaseImpl` modificando `RAgentRowset` heredar de `CMyRowsetImpl`, como se indica a continuación:  
  
```  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CMyProviderCommand>  
```  
  
 `RAgentRowset` Ahora puede usar el `IRowsetLocate` interfaz mientras aprovecha el resto de la implementación de la clase de conjunto de filas.  
  
 Cuando esto sucede, puede [determinar dinámicamente las columnas que se devuelven al consumidor](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Vea también  
 [Mejorar un proveedor sencillo de solo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)