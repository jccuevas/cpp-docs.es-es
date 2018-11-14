---
title: Leer cadenas desde el proveedor OLE DB
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
ms.openlocfilehash: 6d8558cce3fc4818d3e6fc8d64a4c682f5ce5b26
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556171"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>Leer cadenas desde el proveedor OLE DB

El `CCustomRowset::Execute` función abre un archivo y lee las cadenas. El consumidor pasa el nombre de archivo al proveedor mediante una llamada a [ICommandText:: SetCommandText](https://docs.microsoft.com/previous-versions/windows/desktop/ms709757(v=vs.85)). El proveedor recibe el nombre de archivo y lo almacena en la variable miembro `m_strCommandText`. `Execute` lee el nombre del archivo `m_strCommandText`. Si el nombre de archivo no es válido o no está disponible, el archivo `Execute` devuelve un error. En caso contrario, se abre el archivo y las llamadas `fgets` para recuperar las cadenas. Para cada conjunto de cadenas se lee, `Execute` crea una instancia del registro de usuario (modificado `CCustomWindowsFile` desde [almacenar cadenas en el proveedor OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md)) y lo coloca en una matriz.

Si no se puede abrir el archivo, `Execute` debe devolver DB_E_NOTABLE. Si devuelve E_FAIL en su lugar, el proveedor no funcionará con muchos consumidores y no se transfiera OLE DB [las pruebas de conformidad](../../data/oledb/testing-your-provider.md).

## <a name="example"></a>Ejemplo

```cpp
/////////////////////////////////////////////////////////////////////////
// CustomRS.h
class CCustomRowset : public CRowsetImpl< CCustomRowset, CCustomWindowsFile, CCustomCommand>
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
        size_t nLength;

        ObjectLock lock(this);

        // From a filename, passed in as a command text, scan the file
        // placing data in the data array.
        if (!m_strCommandText)
        {
            ATLTRACE("No filename specified");
            return E_FAIL;
        }

        // Open the file
        _tcscpy_s(szFile, sizeOfFile, m_strCommandText);
        if (szFile[0] == _T('\0') ||
            (fopen_s(&pFile, (char*)&szFile[0], "r") == 0))
        {
            ATLTRACE("Could not open file");
            return DB_E_NOTABLE;
        }

        // Scan and parse the file.
        // The file should contain two strings per record
        LONG cFiles = 0;
        while (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
        {
            nLength = strnlen((char*)szString, sizeOfBuffer);
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF
            CCustomWindowsFile am;
            _tcscpy_s(am.szCommand, am.iSize, szString);
            _tcscpy_s(am.szCommand2, am.iSize, szString);

            if (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
            {
                nLength = strnlen((char*)szString, sizeOfBuffer);
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF
                _tcscpy_s(am.szText, am.iSize, szString);
                _tcscpy_s(am.szText2, am.iSize, szString);
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
};
```

Cuando esto sucede, el proveedor debería estar listo para compilar y ejecutar. Para probar el proveedor, se necesita un consumidor con funcionalidad de coincidencia. [Implementar un consumidor sencillo](../../data/oledb/implementing-a-simple-consumer.md) se muestra cómo crear un consumidor de prueba de este tipo. Ejecute el consumidor de prueba con el proveedor y compruebe que el consumidor de prueba recupera las cadenas apropiadas del proveedor.

Cuando haya comprobado correctamente el proveedor, puede ampliar su funcionalidad mediante la implementación de interfaces adicionales. Se muestra un ejemplo en [mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md).

## <a name="see-also"></a>Vea también

[Implementar un proveedor sencillo de solo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
