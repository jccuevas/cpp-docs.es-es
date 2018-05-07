---
title: CMyProviderWindowsFile | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderwindowsfile
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8f0ba90bdcbaa4255757ee31015d0f6986862916
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmyproviderwindowsfile"></a>CMyProviderWindowsFile
El asistente crea una clase para que contenga una fila de datos; en este caso, se denomina `CMyProviderWindowsFile`. El siguiente código para `CMyProviderWindowsFile` se genera con un asistente y muestra todos los archivos de un directorio mediante la **WIN32_FIND_DATA** estructura. `CMyProviderWindowsFile` hereda de la **WIN32_FIND_DATA** estructura:  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
class CMyProviderWindowsFile:   
   public WIN32_FIND_DATA  
{  
public:  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)  
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)  
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)  
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)  
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)  
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)  
END_PROVIDER_COLUMN_MAP()  
};  
```  
  
 `CMyProviderWindowsFile` se llama a la [clase de registro de usuario](../../data/oledb/user-record.md) porque también contiene un mapa que describe las columnas de conjunto de filas del proveedor. El mapa de columnas del proveedor contiene una entrada para cada campo del conjunto de filas mediante las macros PROVIDER_COLUMN_ENTRY. Las macros especifican el nombre de columna ordinal y el desplazamiento a una entrada de la estructura. Las entradas de la columna de proveedor en el código anterior contienen desplazamientos en la **WIN32_FIND_DATA** estructura. Cuando el consumidor llama **IRowset:: GetData**, los datos se transfieren en un búfer contiguo. En lugar de realizar utilizar aritmética de punteros, el mapa permite especificar un miembro de datos.  
  
 El `CMyProviderRowset` clase también contiene el `Execute` método. `Execute` es lo que realmente lee los datos de origen nativo. El código siguiente muestra los generados por el asistente `Execute` método. La función utiliza el Win32 **FindFirstFile** y `FindNextFile` API para recuperar información acerca de los archivos en el directorio y colocarlos en instancias de la `CMyProviderWindowsFile` clase.  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)  
{  
   USES_CONVERSION;  
   BOOL bFound = FALSE;  
   HANDLE hFile;  
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :  
       OLE2T(m_strCommandText);  
   CMyProviderWindowsFile wf;  
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
  
 El directorio de búsqueda se representa mediante `m_strCommandText`; contiene el texto representado por la `ICommandText` interfaz en el objeto de comando. Si no se especifica ningún directorio, utiliza el directorio actual.  
  
 El método crea una entrada para cada archivo (correspondiente a una fila) y lo coloca en el **m_rgRowData** miembro de datos. El `CRowsetImpl` clase define la **m_rgRowData** miembro de datos. Los datos de esta matriz representan toda la tabla y se usan en las plantillas.  
  
## <a name="see-also"></a>Vea también  
 [Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)