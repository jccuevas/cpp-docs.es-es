---
title: Modificar la herencia de RMyProviderRowset | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 75acbc8370c1ea164c72aa6f0c61a95fe287e3d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106237"
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