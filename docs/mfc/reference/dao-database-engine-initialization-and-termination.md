---
title: Inicialización del motor de base de datos DAO y terminación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f28c0c166bcbf13181161d6afce484fe4a45b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369907"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicialización y terminación del motor de bases de datos DAO
Cuando se usan objetos de DAO de MFC, el motor de base de datos DAO en primer lugar debe inicializar y, a continuación, finaliza antes de que salga de la aplicación o el archivo DLL. Dos funciones, `AfxDaoInit` y `AfxDaoTerm`, realizar estas tareas.  
  
### <a name="dao-database-engine-initialization-and-termination"></a>Inicialización y terminación del motor de bases de datos DAO  
  
|||  
|-|-|  
|[AfxDaoInit](#afxdaoinit)|Inicializa el motor de base de datos DAO.|  
|[AfxDaoTerm](#afxdaoterm)|Finaliza el motor de base de datos DAO.|  
  
##  <a name="afxdaoinit"></a>  AfxDaoInit  
 Esta función inicializa el motor de base de datos DAO.  
  
```  
 
void AfxDaoInit();

throw(CDaoException*);  
```  
  
### <a name="remarks"></a>Comentarios  
 En la mayoría de los casos, no es necesario llamar a `AfxDaoInit` porque la aplicación llama automáticamente a él cuando sea necesario.  
  
 Para obtener información relacionada y para obtener un ejemplo de llamar al método `AfxDaoInit`, consulte [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  
  
##  <a name="afxdaoterm"></a>  AfxDaoTerm  
 Esta función finaliza el motor de base de datos DAO.  
  
```  
 
void AfxDaoTerm();  
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, sólo necesita llamar a esta función en una DLL de MFC; normal una aplicación llama automáticamente a `AfxDaoTerm` cuando sea necesario.  
  
 En archivos DLL de MFC estándar, llamada `AfxDaoTerm` antes de la `ExitInstance` función, pero después de que se han destruido todos los objetos DAO de MFC.  
  
 Para obtener información relacionada, consulte [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
