---
title: Abrir archivos | Documentos de Microsoft
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
ms.openlocfilehash: 379449469d37f01c7c0fd225688a019eaec9e977
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352768"
---
# <a name="opening-files"></a>Abrir archivos
En MFC, la manera más común para abrir un archivo es un proceso de dos fases.  
  
#### <a name="to-open-a-file"></a>Para abrir un archivo  
  
1.  Crear el objeto de archivo sin especificar una ruta de acceso o indicadores de permisos.  
  
     Normalmente se crea un objeto de archivo declarando un [CFile](../mfc/reference/cfile-class.md) variable en el marco de pila.  
  
2.  Llame a la [abiertos](../mfc/reference/cfile-class.md#open) función de miembro para el objeto de archivo, proporcionando una ruta de acceso e indicadores de permisos.  
  
     El valor devuelto para `Open` será distinto de cero si se abrió correctamente el archivo o 0 si no se pudo abrir el archivo especificado. El `Open` es la función miembro el prototipo siguiente:  
  
     `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`  
  
     Las marcas de abrir especifican qué permisos, como de solo lectura, que desea para el archivo. Los valores de indicador posibles se definen como constantes enumeradas en la `CFile` de la clase, por lo que están calificados con "`CFile::`" como en `CFile::modeRead`. Use la `CFile::modeCreate` marcar si desea crear el archivo.  
  
 En el ejemplo siguiente se muestra cómo crear un nuevo archivo con permiso de lectura/escritura (reemplazando cualquier archivo anterior con la misma ruta de acceso):  
  
 [!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]  
  
> [!NOTE]
>  Este ejemplo crea y abre un archivo. Si hay problemas, el `Open` llamada pueda regresar un `CFileException` objeto en su último parámetro, como se muestra aquí. El `TRACE` macro imprime el nombre de archivo y un código que indica el motivo del error. Puede llamar a la `AfxThrowFileException` funcionar si necesita más detallados informes de errores.  
  
## <a name="see-also"></a>Vea también  
 [CFile (clase)](../mfc/reference/cfile-class.md)   
 [CFile::Open](../mfc/reference/cfile-class.md#open)   
 [Archivos](../mfc/files-in-mfc.md)

