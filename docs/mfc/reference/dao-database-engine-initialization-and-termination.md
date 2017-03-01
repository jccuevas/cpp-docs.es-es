---
title: "Inicialización del motor de base de datos DAO y terminación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b6119279234558998fad1f220239a29618c69cc5
ms.lasthandoff: 02/24/2017

---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicialización y terminación del motor de bases de datos DAO
Al utilizar objetos DAO de MFC, el motor de base de datos DAO en primer lugar debe ser inicializado y después termina antes de que salga de la aplicación o DLL. Dos funciones, `AfxDaoInit` y `AfxDaoTerm`, realizar estas tareas.  
  
### <a name="dao-database-engine-initialization-and-termination"></a>Inicialización y terminación del motor de bases de datos DAO  
  
|||  
|-|-|  
|[AfxDaoInit](#afxdaoinit)|Inicializa el motor de base de datos DAO.|  
|[AfxDaoTerm](#afxdaoterm)|Finaliza el motor de base de datos DAO.|  
  
##  <a name="a-nameafxdaoinita--afxdaoinit"></a><a name="afxdaoinit"></a>AfxDaoInit  
 Esta función inicializa el motor de base de datos DAO.  
  
```  
 
void AfxDaoInit();

throw(CDaoException*);  
```  
  
### <a name="remarks"></a>Comentarios  
 En la mayoría de los casos, no es necesario llamar a `AfxDaoInit` porque la aplicación automáticamente llamarla cuando sea necesario.  
  
 Para obtener más información y un ejemplo de llamada `AfxDaoInit`, consulte [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  
  
##  <a name="a-nameafxdaoterma--afxdaoterm"></a><a name="afxdaoterm"></a>AfxDaoTerm  
 Esta función termina el motor de base de datos DAO.  
  
```  
 
void AfxDaoTerm();  
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, sólo necesita llamar a esta función en un archivo DLL; una aplicación llama automáticamente a `AfxDaoTerm` cuando sea necesario.  
  
 En archivos DLL estándar, llamada `AfxDaoTerm` antes de la `ExitInstance` (función), pero después de que se han destruido todos los objetos DAO de MFC.  
  
 Para obtener información relacionada, vea [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdao.h  

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

