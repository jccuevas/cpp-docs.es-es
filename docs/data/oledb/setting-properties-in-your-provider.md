---
title: Establecer propiedades en un proveedor | Documentos de Microsoft
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
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 92c5128e3df1e2dfebfef338f3505201cfc40671
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="setting-properties-in-your-provider"></a>Establecer propiedades en un proveedor
Busque el grupo de propiedades y el identificador de propiedad para la propiedad que desee. Para obtener más información, consulte [propiedades de OLE DB](https://msdn.microsoft.com/en-us/library/ms722734.aspx) en el *referencia del programador de OLE DB*.  
  
 En el código del proveedor generado por el asistente, busque la asignación de propiedad correspondiente al grupo de propiedades. El nombre del grupo de propiedades suele corresponder al nombre del objeto. Propiedades de comando y el conjunto de filas pueden encontrarse en el comando o el conjunto de filas; propiedades de inicialización y el origen de datos pueden encontrarse en el objeto de origen de datos.  
  
 En la asignación de propiedad, agregue un [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md) macro. PROPERTY_INFO_ENTRY_EX utiliza cuatro parámetros:  
  
-   El identificador de propiedad correspondiente a la propiedad. Debe quitar los siete primeros caracteres ("DBPROP_") desde el principio del nombre de la propiedad. Por ejemplo, si desea agregar **DBPROP_MAXROWS**, pasar `MAXROWS` como el primer elemento. Si se trata de una propiedad personalizada, pase el nombre GUID completo (por ejemplo, `DBMYPROP_MYPROPERTY`).  
  
-   El tipo variant de la propiedad (en [propiedades de OLE DB](https://msdn.microsoft.com/en-us/library/ms722734.aspx) en el *referencia del programador de OLE DB*). Escriba el **VT_** tipo (como `VT_BOOL` o `VT_I2`) correspondiente al tipo de datos.  
  
-   Marca para indicar si la propiedad es de lectura y escritura y el grupo al que pertenece. Por ejemplo, el código siguiente indica una propiedad de lectura/escritura que pertenecen al grupo de conjunto de filas:  
  
    ```  
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE  
    ```  
  
-   El valor base de la propiedad. Esto podría ser **VARIANT_FALSE** para un valor booleano escriba o cero para un tipo entero, por ejemplo. La propiedad tiene este valor a menos que se cambie.  
  
    > [!NOTE]
    >  Algunas propiedades están conectadas o encadenadas a otras propiedades, como marcadores o la actualización. Cuando un consumidor establece una propiedad en true, también se puede establecer otra propiedad. Las plantillas de proveedor OLE DB admiten esto mediante el método [CUtlProps:: OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md).  
  
## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Propiedades que se pasa por alto por los proveedores de OLE DB de Microsoft  
 Los proveedores de Microsoft OLE DB pasar por alto las siguientes propiedades de OLE DB:  
  
-   **DBPROP_MAXROWS** solo funciona para los proveedores de sólo lectura (es decir, cuando DBPROP_IRowsetChange y DBPROP_IRowsetUpdate son false); en caso contrario, esta propiedad no es compatible.  
  
-   **DBPROP_MAXPENDINGROWS** se pasa por alto; el proveedor especifica su propio límite.  
  
-   **DBPROP_MAXOPENROWS** se pasa por alto; el proveedor especifica su propio límite.  
  
-   **DBPROP_CANHOLDROWS** se pasa por alto; el proveedor especifica su propio límite.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)