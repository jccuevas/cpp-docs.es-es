---
title: Almacenar cadenas en el proveedor OLE DB | Documentos de Microsoft
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
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 523193d7fa5f18d3d0956d39ca68cdc5d34131b0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Almacenar cadenas en el proveedor OLE DB
En MyProviderRS.h, el Asistente para proveedores OLE DB ATL crea un registro de usuario predeterminado denominado `CWindowsFile`. Para controlar las dos cadenas, modifique `CWindowsFile` o agregue su propio registro de usuario tal como se muestra en el código siguiente:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
class CAgentMan:   
   public WIN32_FIND_DATA  
   DWORD dwBookmark;              // Add this  
   TCHAR szCommand[256];          // Add this  
   TCHAR szText[256];             // Add this  
   TCHAR szCommand2[256];         // Add this  
   TCHAR szText2[256];            // Add this  
  
{  
public:  
BEGIN_PROVIDER_COLUMN_MAP()  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command"), 1, 256, GUID_NULL, CAgentMan, szCommand)  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text"), 2, 256, GUID_NULL, CAgentMan, szText)   
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command2"), 3, 256, GUID_NULL, CAgentMan, szCommand2)  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text2"),4, 256, GUID_NULL, CAgentMan, szText2)  
END_PROVIDER_COLUMN_MAP()  
   bool operator==(const CAgentMan& am) // This is optional   
   {  
      return (lstrcmpi(cFileName, wf.cFileName) == 0);  
   }  
};  
```  
  
 Los miembros de datos `szCommand` y `szText` representan las dos cadenas, con `szCommand2` y `szText2` proporcionan columnas adicionales si es necesario. El miembro de datos `dwBookmark` no es necesario para este proveedor sencillo de sólo lectura, pero se utiliza más adelante para agregar una `IRowsetLocate` interfaz; vea [mejorar lectura solo un proveedor sencillo](../../data/oledb/enhancing-the-simple-read-only-provider.md). El `==` operador compara instancias (la implementación de este operador es opcional).  
  
 Cuando esto sucede, el proveedor debería estar listo para compilarse y ejecutarse. Para probar el proveedor, se necesita un consumidor con funcionalidad de coincidencia. [Implementar un consumidor sencillo](../../data/oledb/implementing-a-simple-consumer.md) muestra cómo crear un consumidor de prueba de este tipo. Ejecute el consumidor de prueba con el proveedor. Compruebe que el consumidor de prueba recupera las cadenas apropiadas del proveedor al hacer clic en el **ejecutar** botón en el **consumidor de prueba** cuadro de diálogo.  
  
 Cuando haya probado con éxito el proveedor, puede ampliar su funcionalidad mediante la implementación de interfaces adicionales. Se muestra un ejemplo en [mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
## <a name="see-also"></a>Vea también  
 [Implementar un proveedor sencillo de solo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md)