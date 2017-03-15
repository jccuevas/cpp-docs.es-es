---
title: "CMyProviderWindowsFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cmyproviderwindowsfile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMyProviderWindowsFile (clase)"
  - "proveedores OLE DB, archivos generados por el asistente"
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CMyProviderWindowsFile
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El asistente crea una clase que contenga una fila de datos; en este caso, se denomina `CMyProviderWindowsFile`.  El siguiente fragmento de código para `CMyProviderWindowsFile` se genera con un asistente y muestra todos los archivos de un directorio mediante la estructura **WIN32\_FIND\_DATA**.  `CMyProviderWindowsFile` hereda de la estructura **WIN32\_FIND\_DATA**:  
  
```  
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
  
 `CMyProviderWindowsFile` es la [clase de registros de usuario](../../data/oledb/user-record.md) porque también contiene un mapa que describe las columnas del conjunto de filas del proveedor.  El mapa de columnas del proveedor contiene una entrada para cada campo del conjunto de filas que utiliza las macros PROVIDER\_COLUMN\_ENTRY.  Las macros especifican el nombre de columna, el ordinal y el desplazamiento a una entrada de la estructura.  Las entradas de columna de proveedor del código anterior contienen desplazamientos en la estructura **WIN32\_FIND\_DATA**.  Cuando el consumidor llama a **IRowset::GetData**, se transfieren los datos a un búfer contiguo.  En lugar de tener que utilizar aritmética de punteros, con el mapa se puede especificar un miembro de datos.  
  
 La clase `CMyProviderRowset` también contiene el método `Execute`.  El método `Execute` es el que lee realmente los datos del origen nativo.  El código siguiente muestra el método `Execute` generado por el asistente.  La función utiliza los API **FindFirstFile** y `FindNextFile` de Win32 para recuperar información acerca de los archivos del directorio y colocarlos en instancias de la clase `CMyProviderWindowsFile`.  
  
```  
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
  
 El directorio en el que se va a buscar se representa mediante `m_strCommandText`; contiene el texto representado por la interfaz `ICommandText` en el objeto de comando.  Si no se especifica ningún directorio, utiliza el directorio actual.  
  
 El método crea una entrada para cada archivo \(correspondiente a una fila\) y la coloca en el miembro de datos **m\_rgRowData**.  La clase `CRowsetImpl` define el miembro de datos **m\_rgRowData**.  Los datos de esta matriz representan la tabla completa y se utilizan en las plantillas.  
  
## Vea también  
 [Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)