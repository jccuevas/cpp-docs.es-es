---
title: Apertura de archivos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f74c0fdcdb8d6dfe1aced33a1c7087ecde6c89ff
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080928"
---
# <a name="opening-files"></a>Abrir archivos

En MFC, la manera más común para abrir un archivo es un proceso de dos fases.

#### <a name="to-open-a-file"></a>Para abrir un archivo

1. Cree el objeto de archivo sin especificar una ruta de acceso o permiso marcadores.

   Suele crear un objeto de archivo declarando un [CFile](../mfc/reference/cfile-class.md) variable en el marco de pila.

1. Llame a la [abierto](../mfc/reference/cfile-class.md#open) función miembro para el objeto de archivo, proporcionando una ruta de acceso e indicadores de permisos.

   El valor devuelto para `Open` será distinto de cero si el archivo se abrió correctamente o 0 si no se pudo abrir el archivo especificado. El `Open` función miembro es el siguiente prototipo:

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Las marcas open especifican qué permisos, como de solo lectura, que desee para el archivo. Los valores de indicador posibles se definen como constantes enumeradas en la `CFile` clase, por lo que se completa con "`CFile::`" como en `CFile::modeRead`. Use el `CFile::modeCreate` marca si desea crear el archivo.

El ejemplo siguiente muestra cómo crear un nuevo archivo con permiso de lectura/escritura (reemplazando cualquier archivo anterior con la misma ruta de acceso):

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
>  En este ejemplo se crea y abre un archivo. Si hay problemas, el `Open` llamada puede devolver un `CFileException` objeto en su último parámetro, como se muestra aquí. La macro TRACE imprime el nombre de archivo y un código que indica el motivo del error. Puede llamar a la `AfxThrowFileException` funcionar si necesita más detallados de informes de errores.

## <a name="see-also"></a>Vea también

[CFile (clase)](../mfc/reference/cfile-class.md)<br/>
[CFile::Open](../mfc/reference/cfile-class.md#open)<br/>
[Archivos](../mfc/files-in-mfc.md)

