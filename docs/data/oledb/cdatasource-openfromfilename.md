---
title: 'CDataSource:: Openfromfilename | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
dev_langs:
- C++
helpviewer_keywords:
- OpenFromFileName method
ms.assetid: c4226de6-59da-4368-9c15-c5afab86f68b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f2d46bbec50bd221115f5645a7dec867900a006a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cdatasourceopenfromfilename"></a>CDataSource::OpenFromFileName
Abre un origen de datos desde un archivo especificado por el nombre de archivo proporcionado por el usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `szFileName`  
 [in] El nombre de un archivo, normalmente una conexión de origen de datos. Archivo (.UDL).  
  
 Para obtener más información acerca de los archivos de vínculo de datos (archivos .udl), consulte [información general sobre la API de vínculos de datos](https://msdn.microsoft.com/en-us/library/ms718102.aspx) del SDK de Windows.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio, como la agrupación de recursos y la inscripción automática de transacciones, entre otras. Para obtener más información, vea "Servicios OLE DB" en referencia del programador de OLE DB de [http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataSource (Clase)](../../data/oledb/cdatasource-class.md)