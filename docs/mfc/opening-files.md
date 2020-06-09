---
title: Abrir archivos
ms.date: 11/04/2016
helpviewer_keywords:
- Open member functions [MFC]
- CFile class [MFC], variable
- opening files, in MFC
- Open calls [MFC]
- Open method, CFile class [MFC]
- examples [MFC], opening files
- opening files, handling exceptions
- exception handling [MFC], when opening files
- files [MFC], opening
- file objects [MFC]
- MFC, file operations
- opening files [MFC]
- exception handling [MFC], opening files
ms.assetid: a991b8ec-b04a-4766-b47e-7485b5dd0b01
ms.openlocfilehash: 73407eba802b7640e880b821144954fa6442f177
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622164"
---
# <a name="opening-files"></a>Abrir archivos

En MFC, la manera más común de abrir un archivo es un proceso de dos fases.

#### <a name="to-open-a-file"></a>Para abrir un archivo

1. Cree el objeto de archivo sin especificar una ruta de acceso o marcas de permisos.

   Normalmente, se crea un objeto de archivo mediante la declaración de una variable [CFile](reference/cfile-class.md) en el marco de pila.

1. Llame a la función miembro [Open](reference/cfile-class.md#open) del objeto de archivo y proporcione una ruta de acceso y marcas de permisos.

   El valor devuelto para `Open` será distinto de cero si el archivo se abrió correctamente o 0 si no se pudo abrir el archivo especificado. El `Open` prototipo de la función miembro es el siguiente:

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Las marcas de apertura especifican los permisos, como solo lectura, que desea para el archivo. Los valores de marca posibles se definen como constantes enumeradas en la `CFile` clase, por lo que se califican con " `CFile::` " como en `CFile::modeRead` . Use la `CFile::modeCreate` marca si desea crear el archivo.

En el ejemplo siguiente se muestra cómo crear un nuevo archivo con permiso de lectura y escritura (reemplazando cualquier archivo anterior con la misma ruta de acceso):

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> En este ejemplo se crea y se abre un archivo. Si hay problemas, la `Open` llamada puede devolver un `CFileException` objeto en su último parámetro, como se muestra aquí. La macro TRACE imprime el nombre de archivo y un código que indica la razón del error. Puede llamar a la `AfxThrowFileException` función si necesita informes de errores más detallados.

## <a name="see-also"></a>Consulte también

[CFile (clase)](reference/cfile-class.md)<br/>
[CFile:: Open](reference/cfile-class.md#open)<br/>
[Archivos](files-in-mfc.md)
