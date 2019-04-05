---
title: Almacenar cadenas en el proveedor OLE DB
ms.date: 10/26/2018
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: 5dce7dac84ef69da17baac135a68bd78698c4456
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026414"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Almacenar cadenas en el proveedor OLE DB

En *personalizado*RS.h, el **el Asistente para proveedores OLE DB ATL** crea un registro de usuario predeterminado denominado `CWindowsFile`. Para controlar las dos cadenas, modificar `CWindowsFile` tal como se muestra en el código siguiente:

```cpp
////////////////////////////////////////////////////////////////////////
class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
DWORD dwBookmark;
static const int iSize = 256;    // Add this
TCHAR szCommand[iSize];          // Add this
TCHAR szText[iSize];             // Add this
TCHAR szCommand2[iSize];         // Add this
TCHAR szText2[iSize];            // Add this

BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)

   PROVIDER_COLUMN_ENTRY_STR("Command", 6, szCommand)    // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text", 7, szText)          // Add this
   PROVIDER_COLUMN_ENTRY_STR("Command2", 8, szCommand2)  // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text2", 9, szText2)        // Add this
END_PROVIDER_COLUMN_MAP()

   bool operator==(const CCustomWindowsFile& am) // This is optional
   {
      return (lstrcmpi(cFileName, am.cFileName) == 0);
   }
};
```

Los miembros de datos `szCommand` y `szText` representan las dos cadenas, con `szCommand2` y `szText2` con columnas adicionales si es necesario. El miembro de datos `dwBookmark` no es necesario para este proveedor sencillo de sólo lectura, pero se utiliza posteriormente para agregar una `IRowsetLocate` interfaz; vea [mejorar lectura solo un proveedor sencillo](../../data/oledb/enhancing-the-simple-read-only-provider.md). El `==` operador compara instancias (implementación de este operador es opcional).

Cuando esto sucede, puede agregar la funcionalidad de [leer cadenas desde el proveedor OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).

## <a name="see-also"></a>Vea también

[Implementar un proveedor sencillo de sólo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
