---
title: "Establecer propiedades en un proveedor | Microsoft Docs"
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
  - "proveedores OLE DB, propiedades"
  - "propiedades [C++], proveedor OLE DB"
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Establecer propiedades en un proveedor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Busque el grupo de propiedades y el identificador de propiedad para la propiedad que desee.  Para obtener más información, vea [Propiedades de OLE DB](https://msdn.microsoft.com/en-us/library/ms722734.aspx) en la *Referencia del programador de OLE DB*.  
  
 En el código del proveedor generado por el asistente, busque el mapa de propiedades correspondiente al grupo de propiedades.  El nombre del grupo de propiedades suele corresponder al nombre del objeto.  Encontrará las propiedades de comando y de conjunto de filas en el comando o el conjunto de filas; encontrará las propiedades de origen de datos y de inicialización en el objeto de origen de datos.  
  
 En el mapa de propiedades, agregue una macro [PROPERTY\_INFO\_ENTRY\_EX](../../data/oledb/property-info-entry-ex.md).  PROPERTY\_INFO\_ENTRY\_EX utiliza cuatro parámetros:  
  
-   El identificador de propiedad correspondiente a la propiedad.  Debe quitar los siete primeros caracteres \("DBPROP\_"\) del principio del nombre de propiedad.  Por ejemplo, si desea agregar **DBPROP\_MAXROWS**, pase `MAXROWS` como primer elemento.  Si se trata de una propiedad personalizada, pase el nombre de GUID completo \(por ejemplo, `DBMYPROP_MYPROPERTY`\).  
  
-   El tipo Variant de la propiedad \(en [Propiedades de OLE DB](https://msdn.microsoft.com/en-us/library/ms722734.aspx), en la *Referencia del programador de OLE DB*\).  Escriba el tipo **VT\_** \(como `VT_BOOL` o `VT_I2`\) correspondiente al tipo de datos.  
  
-   Marcadores que muestran si la propiedad es de lectura y escritura, y el grupo al que pertenece.  Por ejemplo, el siguiente fragmento de código indica una propiedad de lectura y escritura que pertenece al grupo conjunto de filas:  
  
    ```  
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE  
    ```  
  
-   El valor base de la propiedad.  Puede ser **VARIANT\_FALSE** para un tipo Boolean o cero para un tipo entero, por ejemplo.  La propiedad tiene este valor a menos que se modifique.  
  
    > [!NOTE]
    >  Algunas propiedades están conectadas o encadenadas a otras propiedades, como los marcadores o la actualización.  Cuando un consumidor establece el valor de una propiedad en true, es posible que se establezca también otra propiedad.  Las plantillas de proveedor OLE DB admiten esto mediante el método [CUtlProps::OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md).  
  
## Propiedades omitidas por los proveedores de Microsoft OLE DB  
 Los proveedores de Microsoft OLE DB omiten las siguientes propiedades de OLE DB:  
  
-   **DBPROP\_MAXROWS** únicamente trabaja con proveedores de sólo lectura \(es decir, cuando DBPROP\_IRowsetChange y DBPROP\_IRowsetUpdate son false\); en caso contrario, esta propiedad no es compatible.  
  
-   **DBPROP\_MAXPENDINGROWS** se omite; el proveedor especifica su propio límite.  
  
-   **DBPROP\_MAXOPENROWS** se omite; el proveedor especifica su propio límite.  
  
-   **DBPROP\_CANHOLDROWS** se omite; el proveedor especifica su propio límite.  
  
## Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)