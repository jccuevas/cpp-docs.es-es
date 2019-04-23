---
title: Modificar la herencia de RCustomRowset
ms.date: 10/26/2018
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
- RCustomRowset
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
ms.openlocfilehash: d22c6902667ec84abe7bd85ffbffd1f5c5c57f2a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024873"
---
# <a name="modifying-the-inheritance-of-rcustomrowset"></a>Modificar la herencia de RCustomRowset

Para agregar la `IRowsetLocate` de la interfaz para el ejemplo de proveedor sencillo de sólo lectura, modifique la herencia de `CCustomRowset`. Inicialmente, `CCustomRowset` hereda de `CRowsetImpl`. Tiene que modificarlo para heredar de `CRowsetBaseImpl`.

Para ello, cree una nueva clase, `CCustomRowsetImpl`, en *personalizado*RS.h:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>
{
...
};
```

Ahora, edite el mapa de interfaz COM en *personalizado*RS.h a ser como sigue:

```cpp
BEGIN_COM_MAP(CMyRowsetImpl)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

Este código crea un mapa de interfaz COM que se indica a `CMyRowsetImpl` para llamar a `QueryInterface` tanto para el `IRowset` y `IRowsetLocate` interfaces. Para obtener toda la implementación para el conjunto de filas de otra clases, los vínculos del mapa la `CMyRowsetImpl` clase nuevo a la `CRowsetBaseImpl` clase definida por las plantillas OLE DB; el mapa utiliza la macro COM_INTERFACE_ENTRY_CHAIN, que indica a las plantillas OLE DB para analizar el mapa COM `CRowsetBaseImpl` en respuesta a un `QueryInterface` llamar.

Por último, vincule `CCustomRowset` a `CMyRowsetBaseImpl` modificando `CCustomRowset` va a heredar `CMyRowsetImpl`, como sigue:

```cpp
class CCustomRowset : public CMyRowsetImpl<CCustomRowset, CCustomWindowsFile, CCustomCommand>
```

`CCustomRowset` Ahora puede usar el `IRowsetLocate` interfaz al tiempo que aprovecha el resto de la implementación de la clase de conjunto de filas.

Cuando esto sucede, puede [determinar dinámicamente las columnas que se devuelven al consumidor](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Vea también

[Mejorar un proveedor sencillo de solo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
