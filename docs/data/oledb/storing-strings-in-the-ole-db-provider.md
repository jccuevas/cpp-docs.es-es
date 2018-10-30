---
title: Almacenar cadenas en el proveedor OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 46529a97ff38071c71ecdaf93e41f3eeb405c8a6
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216440"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Almacenar cadenas en el proveedor OLE DB

MyProviderRS.h, el **el Asistente para proveedores OLE DB ATL** crea un registro de usuario predeterminado denominado `CWindowsFile`. Para controlar las dos cadenas, modifique `CWindowsFile` o agregue su propio registro de usuario, como se muestra en el código siguiente:

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

Los miembros de datos `szCommand` y `szText` representan las dos cadenas, con `szCommand2` y `szText2` con columnas adicionales si es necesario. El miembro de datos `dwBookmark` no es necesario para este proveedor sencillo de sólo lectura, pero se utiliza posteriormente para agregar una `IRowsetLocate` interfaz; vea [mejorar lectura solo un proveedor sencillo](../../data/oledb/enhancing-the-simple-read-only-provider.md). El `==` operador compara instancias (implementación de este operador es opcional).

Cuando esto sucede, el proveedor debería estar listo para compilar y ejecutar. Para probar el proveedor, se necesita un consumidor con funcionalidad de coincidencia. [Implementar un consumidor sencillo](../../data/oledb/implementing-a-simple-consumer.md) se muestra cómo crear un consumidor de prueba de este tipo. Ejecute el consumidor de prueba con el proveedor. Compruebe que el consumidor de prueba recupera las cadenas apropiadas del proveedor al hacer clic en el **ejecutar** situado en la **probar consumidor** cuadro de diálogo.

Cuando haya comprobado correctamente el proveedor, puede ampliar su funcionalidad mediante la implementación de interfaces adicionales. Se muestra un ejemplo en [mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md).

## <a name="see-also"></a>Vea también

[Implementar un proveedor sencillo de solo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
