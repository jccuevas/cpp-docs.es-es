---
title: CCustomWindowsFile
ms.date: 10/22/2018
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
ms.openlocfilehash: 4af302d8a391de359f3b8ac66d41b5d7198fd8f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182917"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

El asistente crea una clase que tiene una fila de datos. en este caso, se llama `CCustomWindowsFile`. El siguiente código para `CCustomWindowsFile` es asistente que se genera y muestra todos los archivos en un directorio mediante la `WIN32_FIND_DATA` estructura. `CCustomWindowsFile` hereda el `WIN32_FIND_DATA` estructura:

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

class CCustomWindowsFile: 
   public WIN32_FIND_DATA
{
public:
BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
};
```

`CCustomWindowsFile` se llama a la [clase de registro de usuario](../../data/oledb/user-record.md) porque también tiene un mapa que describe las columnas de conjunto de filas del proveedor. El mapa de columnas del proveedor contiene una entrada para cada campo del conjunto de filas mediante las macros PROVIDER_COLUMN_ENTRY. Las macros de especifican el nombre de columna ordinal y el desplazamiento a una entrada de la estructura. Las entradas de la columna de proveedor en el código anterior contienen desplazamientos a la `WIN32_FIND_DATA` estructura. Cuando el consumidor llama a `IRowset::GetData`, se transfieren los datos en un búfer contiguo. En lugar de realizar realizar aritmética de puntero, el mapa permite especificar a un miembro de datos.

El `CCustomRowset` clase también contiene el `Execute` método. `Execute` es lo que realmente lee los datos en el origen nativo. El código siguiente muestra el asistente generó `Execute` método. La función usa Win32 `FindFirstFile` y `FindNextFile` API para recuperar información acerca de los archivos en el directorio y colocarlos en las instancias de la `CCustomWindowsFile` clase.

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
{
   USES_CONVERSION;
   BOOL bFound = FALSE;
   HANDLE hFile;
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :
       OLE2T(m_strCommandText);
   CCustomWindowsFile wf;
   hFile = FindFirstFile(szDir, &wf);
   if (hFile == INVALID_HANDLE_VALUE)
      return DB_E_ERRORSINCOMMAND;
   LONG cFiles = 1;
   BOOL bMoreFiles = TRUE;
   while (bMoreFiles)
   {
      if (!m_rgRowData.Add(wf))
         return E_OUTOFMEMORY;
      bMoreFiles = FindNextFile(hFile, &wf);
      cFiles++;
   }
   FindClose(hFile);
   if (pcRowsAffected != NULL)
      *pcRowsAffected = cFiles;
   return S_OK;
}
```

El directorio de búsqueda se muestra mediante `m_strCommandText`; este archivo contiene el texto representado por la `ICommandText` interfaz en el objeto de comando. Si no se especifica ningún directorio, utiliza el directorio actual.

El método crea una entrada para cada archivo (correspondiente a una fila) y lo coloca en el `m_rgRowData` miembro de datos. El `CRowsetImpl` clase define la `m_rgRowData` miembro de datos. Los datos de esta matriz se muestran toda la tabla y se utilizan a lo largo de las plantillas.

## <a name="see-also"></a>Vea también

[Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)<br/>
