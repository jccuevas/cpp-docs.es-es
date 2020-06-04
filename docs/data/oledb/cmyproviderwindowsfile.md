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
ms.openlocfilehash: 103a1ce5568c6137994056e574ce8eec04511d8f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079739"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

El asistente crea una clase que tiene una fila de datos; en este caso, se denomina `CCustomWindowsFile`. El código siguiente para `CCustomWindowsFile` es el asistente generado y enumera todos los archivos de un directorio mediante la estructura `WIN32_FIND_DATA`. `CCustomWindowsFile` hereda de la estructura de `WIN32_FIND_DATA`:

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

`CCustomWindowsFile` se denomina [clase de registro de usuario](../../data/oledb/user-record.md) porque también tiene un mapa que describe las columnas del conjunto de filas del proveedor. El mapa de columnas de proveedor contiene una entrada para cada campo del conjunto de filas mediante las macros PROVIDER_COLUMN_ENTRY. Las macros especifican el nombre de columna, el ordinal y el desplazamiento para una entrada de estructura. Las entradas de columna del proveedor en el código anterior contienen desplazamientos en la estructura de `WIN32_FIND_DATA`. Cuando el consumidor llama a `IRowset::GetData`, los datos se transfieren en un búfer contiguo. En lugar de realizar operaciones aritméticas de puntero, el mapa permite especificar un miembro de datos.

La clase `CCustomRowset` también contiene el método `Execute`. `Execute` es lo que realmente Lee los datos de desde el origen nativo. En el código siguiente se muestra el método de `Execute` generado por el asistente. La función utiliza las API de `FindFirstFile` y `FindNextFile` de Win32 para recuperar información acerca de los archivos del directorio y colocarlos en instancias de la clase `CCustomWindowsFile`.

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

El directorio que se va a buscar se muestra en `m_strCommandText`; contiene el texto representado por la interfaz `ICommandText` en el objeto de comando. Si no se especifica ningún directorio, utiliza el directorio actual.

El método crea una entrada para cada archivo (correspondiente a una fila) y la coloca en el miembro de datos `m_rgRowData`. La clase `CRowsetImpl` define el miembro de datos `m_rgRowData`. Los datos de esta matriz se muestran en toda la tabla y se utilizan en las plantillas.

## <a name="see-also"></a>Consulte también

[Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)<br/>
