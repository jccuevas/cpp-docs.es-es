---
title: Establecer propiedades en un proveedor
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 905a9bb32544dbd7453d46362e100047516d22a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209578"
---
# <a name="setting-properties-in-your-provider"></a>Establecer propiedades en un proveedor

Busque el grupo de propiedades y el identificador de propiedad de la propiedad que desee. Para obtener más información, vea [OLE DB Properties](/previous-versions/windows/desktop/ms722734(v=vs.85)) en la **Referencia del programador de OLE DB**.

En el código de proveedor generado por el asistente, busque la asignación de propiedad correspondiente al grupo de propiedades. El nombre del grupo de propiedades suele corresponder al nombre del objeto. Las propiedades del comando y del conjunto de filas se pueden encontrar en el comando o en el conjunto de filas; los orígenes de datos y las propiedades de inicialización se pueden encontrar en el objeto de origen de datos.

En el mapa de propiedades, agregue una macro [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md) . PROPERTY_INFO_ENTRY_EX toma cuatro parámetros:

- IDENTIFICADOR de propiedad correspondiente a la propiedad. Quite los siete primeros caracteres ("DBPROP_") de la parte delantera del nombre de la propiedad. Por ejemplo, si desea agregar `DBPROP_MAXROWS`, pase `MAXROWS` como primer elemento. Si se trata de una propiedad personalizada, pase el nombre del GUID completo (por ejemplo, `DBMYPROP_MYPROPERTY`).

- Tipo Variant de la propiedad (en [OLE DB propiedades](/previous-versions/windows/desktop/ms722734(v=vs.85)) de la **Referencia del programador de OLE DB**). Especifique el tipo de VT_ (como VT_BOOL o VT_I2) correspondiente al tipo de datos.

- Marcas para indicar si la propiedad se puede leer y escribir y el grupo al que pertenece. Por ejemplo, el código siguiente indica una propiedad de lectura y escritura que pertenece al grupo del conjunto de filas:

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- Valor base de la propiedad. Esto podría ser `VARIANT_FALSE` para un tipo booleano o cero para un tipo entero, por ejemplo. La propiedad tiene este valor a menos que se cambie.

    > [!NOTE]
    > Algunas propiedades están conectadas o encadenadas a otras propiedades, como marcadores o actualizaciones. Cuando un consumidor establece una propiedad en true, también se puede establecer otra propiedad. Las plantillas de proveedor de OLE DB admiten esto a través del método [CUtlProps:: OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md).

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Propiedades omitidas por los proveedores de Microsoft OLE DB

Los proveedores de Microsoft OLE DB omiten las siguientes propiedades de OLE DB:

- `DBPROP_MAXROWS` solo funciona para los proveedores de solo lectura (es decir, donde `DBPROP_IRowsetChange` y `DBPROP_IRowsetUpdate` son **false**); de lo contrario, no se admite esta propiedad.

- `DBPROP_MAXPENDINGROWS` se omite; el proveedor especifica su propio límite.

- `DBPROP_MAXOPENROWS` se omite; el proveedor especifica su propio límite.

- `DBPROP_CANHOLDROWS` se omite; el proveedor especifica su propio límite.

## <a name="see-also"></a>Consulte también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
