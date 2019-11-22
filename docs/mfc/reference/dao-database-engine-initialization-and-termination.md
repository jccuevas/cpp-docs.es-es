---
title: Inicialización y terminación del motor de bases de datos DAO
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 24a24d5a81da18d01472fc760c2adf96ee9868d5
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303456"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicialización y terminación del motor de bases de datos DAO

DAO se utiliza con bases de datos de Access y se admite a través de Office 2013. DAO 3,6 es la versión final y se considera obsoleta. Al utilizar objetos DAO de MFC, primero se debe inicializar el motor de base de datos DAO y después finalizar antes de que se cierre la aplicación o el archivo DLL. Dos funciones, `AfxDaoInit` y `AfxDaoTerm`, realizan estas tareas.

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

En la mayoría de los casos, no es necesario llamar a `AfxDaoInit` porque la aplicación lo llama automáticamente cuando es necesario.

Para obtener información relacionada y un ejemplo de llamada a `AfxDaoInit`, vea la [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao. h

##  <a name="afxdaoterm"></a>  AfxDaoTerm

Esta función finaliza el motor de base de datos DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Comentarios

Normalmente, solo es necesario llamar a esta función en un archivo DLL de MFC normal; una aplicación llamará automáticamente a `AfxDaoTerm` cuando sea necesario.

En archivos dll de MFC normales, llame a `AfxDaoTerm` antes de la función `ExitInstance`, pero después de que se hayan destruido todos los objetos DAO de MFC.

Para obtener información relacionada, vea la [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao. h

## <a name="see-also"></a>Vea también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
