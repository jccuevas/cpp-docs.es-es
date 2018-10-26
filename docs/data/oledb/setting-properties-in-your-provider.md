---
title: Establecer propiedades en un proveedor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7555e90a6eca9c9f4031458963ff2a90eed552a7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057847"
---
# <a name="setting-properties-in-your-provider"></a>Establecer propiedades en un proveedor

Busque el grupo de propiedades y el identificador de propiedad para la propiedad que desee. Para obtener más información, consulte [propiedades de OLE DB](/previous-versions/windows/desktop/ms722734) en el *referencia del programador de OLE DB*.

En el código del proveedor generado por el asistente, busque la asignación de propiedad correspondiente al grupo de propiedades. El nombre del grupo de propiedades normalmente corresponde al nombre del objeto. Propiedades de comando y conjunto de filas pueden encontrarse en el comando o un conjunto de filas; propiedades de inicialización y el origen de datos pueden encontrarse en el objeto de origen de datos.

En el mapa de propiedades, agregue un [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md) macro. PROPERTY_INFO_ENTRY_EX toma cuatro parámetros:

- El identificador de propiedad correspondiente a la propiedad. Debe quitar los siete primeros caracteres ("DBPROP_") desde el principio del nombre de la propiedad. Por ejemplo, si desea agregar `DBPROP_MAXROWS`, pasar `MAXROWS` como el primer elemento. Si se trata de una propiedad personalizada, pase el nombre completo de GUID (por ejemplo, `DBMYPROP_MYPROPERTY`).

- El tipo de variante de la propiedad (en [propiedades de OLE DB](/previous-versions/windows/desktop/ms722734) en el *referencia del programador de OLE DB*). Escriba el tipo VT_ (como VT_BOOL o VT_I2) correspondiente al tipo de datos.

- Marcadores que indican si la propiedad es de lectura y escritura y el grupo al que pertenece. Por ejemplo, el código siguiente indica una propiedad de lectura/escritura que pertenecen al grupo de filas:

    ```
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- El valor de la base de la propiedad. Esto podría ser `VARIANT_FALSE` para un valor booleano, tipo o cero para un tipo entero, por ejemplo. La propiedad tiene este valor a menos que lo cambie.

    > [!NOTE]
    >  Algunas propiedades están conectadas o cadena a otras propiedades, como marcadores o la actualización. Cuando un consumidor establece una propiedad en true, también se puede establecer otra propiedad. Las plantillas de proveedor OLE DB admiten esto mediante el método [CUtlProps:: OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md).

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Propiedades que se pasa por alto por proveedores de OLE DB de Microsoft

Los proveedores OLE DB de Microsoft omitir las siguientes propiedades de OLE DB:

- `DBPROP_MAXROWS` solo funciona para los proveedores de sólo lectura (es decir, cuando DBPROP_IRowsetChange y DBPROP_IRowsetUpdate son false); en caso contrario, no se admite esta propiedad.

- `DBPROP_MAXPENDINGROWS` se omite; el proveedor especifica su propio límite.

- `DBPROP_MAXOPENROWS` se omite; el proveedor especifica su propio límite.

- `DBPROP_CANHOLDROWS` se omite; el proveedor especifica su propio límite.

## <a name="see-also"></a>Vea también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)