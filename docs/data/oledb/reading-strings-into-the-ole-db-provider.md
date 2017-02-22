---
title: "Leer cadenas desde el proveedor OLE DB | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "proveedores OLE DB, leer cadenas"
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Leer cadenas desde el proveedor OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función `RMyProviderRowset::Execute` abre un archivo y lee cadenas.  El consumidor pasa el nombre del archivo al proveedor llamando a [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx).  El proveedor recibe el nombre de archivo y lo almacena en la variable miembro `m_szCommandText`.  `Execute` lee el nombre de archivo de `m_szCommandText`.  Si el nombre de archivo no es válido o el archivo no está disponible, `Execute` devuelve un error.  En caso contrario, abre el archivo y llama a `fgets` para recuperar las cadenas.  Por cada conjunto de cadenas que lee, `Execute` crea una instancia del registro de usuario \(`CAgentMan`\) y la coloca en una matriz.  
  
 Si no se puede abrir el archivo, `Execute` debe devolver **DB\_E\_NOTABLE**.  Si en lugar de ello devuelve **E\_FAIL**, el proveedor no trabajará con muchos consumidores y no superará las [pruebas de conformidad](../../data/oledb/testing-your-provider.md) de OLE DB.  
  
## Ejemplo  
  
### Descripción  
 La función `Execute` modificada ofrece el siguiente aspecto:  
  
### Código  
  
```  
/////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
class RMyProviderRowset : public CRowsetImpl< RMyProviderRowset, CAgentMan, CRMyProviderCommand>  
{  
public:  
    HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)  
    {  
        enum {  
            sizeOfBuffer = 256,  
            sizeOfFile = MAX_PATH  
        };  
        USES_CONVERSION;  
        FILE* pFile = NULL;  
        TCHAR szString[sizeOfBuffer];  
        TCHAR szFile[sizeOfFile];  
        size_t nLength;        errcodeerr;  
  
        ObjectLock lock(this);  
  
        // From a filename, passed in as a command text, scan the file  
        // placing data in the data array.  
        if (!m_szCommandText)  
        {  
            ATLTRACE("No filename specified");  
            return E_FAIL;  
        }  
  
        // Open the file  
        _tcscpy_s(szFile, sizeOfFile, m_szCommandText);  
        if (szFile[0] == _T('\0') ||   
            ((err = fopen_s(&pFile, &szFile[0], "r")) == 0))  
        {  
            ATLTRACE("Could not open file");  
            return DB_E_NOTABLE;  
        }  
  
        // Scan and parse the file.  
        // The file should contain two strings per record  
        LONG cFiles = 0;  
        while (fgets(szString, sizeOfBuffer, pFile) != NULL)  
        {  
            nLength = strnlen(szString, sizeOfBuffer);  
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF  
            CAgentMan am;  
            _tcscpy_s(am.szCommand, am.sizeOfCommand, szString);  
            _tcscpy_s(am.szCommand2, am.sizeOfCommand2, szString);  
  
            if (fgets(szString, sizeOfBuffer, pFile) != NULL)  
            {  
                nLength = strnlen(szString, sizeOfBuffer);  
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF  
                _tcscpy_s(am.szText, am.sizeOfText, szString);  
                _tcscpy_s(am.szText2, am.sizeOfText2, szString);  
            }  
  
            am.dwBookmark = ++cFiles;  
            if (!m_rgRowData.Add(am))  
            {  
                ATLTRACE("Couldn't add data to array");  
                fclose(pFile);  
                return E_FAIL;  
            }  
        }  
  
        if (pcRowsAffected != NULL)  
            *pcRowsAffected = cFiles;  
        return S_OK;  
    }  
}  
```  
  
## Vea también  
 [Implementar un proveedor sencillo de sólo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md)