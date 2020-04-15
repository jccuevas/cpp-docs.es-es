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
ms.openlocfilehash: 6119bf922b05c30a14d8421800e3931c4a038779
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375959"
---
# <a name="opening-files"></a>Abrir archivos

En MFC, la forma más común de abrir un archivo es un proceso de dos etapas.

#### <a name="to-open-a-file"></a>Para abrir un archivo

1. Cree el objeto de archivo sin especificar una ruta de acceso o marcas de permiso.

   Normalmente se crea un objeto de archivo declarando una variable [CFile](../mfc/reference/cfile-class.md) en el marco de pila.

1. Llame a la [Open](../mfc/reference/cfile-class.md#open) función miembro para el objeto de archivo, proporcionando una ruta de acceso y marcas de permiso.

   El valor `Open` devuelto para será distinto de cero si el archivo se abrió correctamente o 0 si no se pudo abrir el archivo especificado. La `Open` función miembro se prototipo de la siguiente manera:

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Las marcas abiertas especifican qué permisos, como de solo lectura, desea para el archivo. Los valores de marca posibles se definen como constantes enumeradas dentro de la `CFile` clase, por lo que se califican con "`CFile::`" como en `CFile::modeRead`. Utilice `CFile::modeCreate` la marca si desea crear el archivo.

En el ejemplo siguiente se muestra cómo crear un nuevo archivo con permiso de lectura y escritura (reemplazando cualquier archivo anterior con la misma ruta de acceso):

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> En este ejemplo se crea y se abre un archivo. Si hay problemas, `Open` la llamada `CFileException` puede devolver un objeto en su último parámetro, como se muestra aquí. La macro TRACE imprime el nombre de archivo y un código que indica el motivo del error. Puede llamar `AfxThrowFileException` a la función si necesita informes de errores más detallados.

## <a name="see-also"></a>Consulte también

[CFile (clase)](../mfc/reference/cfile-class.md)<br/>
[CFile::Abrir](../mfc/reference/cfile-class.md#open)<br/>
[Archivos](../mfc/files-in-mfc.md)
