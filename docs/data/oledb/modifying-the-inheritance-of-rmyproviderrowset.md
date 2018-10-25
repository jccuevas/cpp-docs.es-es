---
title: Modificar la herencia de RCustomRowset | Microsoft Docs
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
- RCustomRowset
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1a9b6e238d3824451ab0f820917c34c97826ffab
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060395"
---
# <a name="modifying-the-inheritance-of-rcustomrowset"></a>Modificar la herencia de RCustomRowset

Para agregar la `IRowsetLocate` de la interfaz para el ejemplo de proveedor sencillo de sólo lectura, modifique la herencia de `RCustomRowset`. Inicialmente, `RCustomRowset` hereda de `CRowsetImpl`. Tiene que modificarlo para heredar de `CRowsetBaseImpl`.

Para ello, cree una nueva clase, `CCustomRowsetImpl`, en CustomRS.h:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>
class CCustomRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>
{
...
};
```

Ahora, edite el mapa de interfaz COM en CustomRS.h ser como sigue:

```cpp
BEGIN_COM_MAP(CCustomRowsetImpl)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

Esto crea un mapa de interfaz COM que se indica a `CCustomRowsetImpl` para llamar a `QueryInterface` tanto para el `IRowset` y `IRowsetLocate` interfaces. Para obtener toda la implementación para el conjunto de filas de otra clases, los vínculos del mapa la `CCustomRowsetImpl` clase nuevo a la `CRowsetBaseImpl` clase definida por las plantillas OLE DB; el mapa utiliza la macro COM_INTERFACE_ENTRY_CHAIN, que indica a las plantillas OLE DB para analizar el mapa COM `CRowsetBaseImpl` en respuesta a un `QueryInterface` llamar.

Por último, vincule `RAgentRowset` a `CCustomRowsetBaseImpl` modificando `RAgentRowset` va a heredar `CCustomRowsetImpl`, como sigue:

```cpp
class RAgentRowset : public CCustomRowsetImpl<RAgentRowset, CAgentMan, CCustomCommand>
```

`RAgentRowset` Ahora puede usar el `IRowsetLocate` interfaz al tiempo que aprovecha el resto de la implementación de la clase de conjunto de filas.

Cuando esto sucede, puede [determinar dinámicamente las columnas que se devuelven al consumidor](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Vea también

[Mejorar un proveedor sencillo de solo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)