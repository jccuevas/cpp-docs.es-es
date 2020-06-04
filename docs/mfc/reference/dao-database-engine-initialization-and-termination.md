---
title: Inicialización y terminación del motor de bases de datos DAO
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 62460e8e55f70b8cb0743f1d044636d25121050d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365890"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicialización y terminación del motor de bases de datos DAO

DAO se usa con bases de datos de Access y se admite a través de Office 2013. DAO 3.6 es la versión final, y se considera obsoleto. Cuando se utilizan objetos DAO de MFC, el motor de base de datos DAO debe inicializarse primero y, a continuación, finalizar antes de que se cierre la aplicación o DLL. Dos `AfxDaoInit` funciones `AfxDaoTerm`y , realizan estas tareas.

### <a name="dao-database-engine-initialization-and-termination"></a>Inicialización y terminación del motor de bases de datos DAO

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|Inicializa el motor de base de datos DAO.|
|[AfxDaoTerm](#afxdaoterm)|Termina el motor de base de datos DAO.|

## <a name="afxdaoinit"></a><a name="afxdaoinit"></a>AfxDaoInit

Esta función inicializa el motor de base de datos DAO.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Observaciones

En la mayoría de los casos, no es necesario llamar `AfxDaoInit` porque la aplicación lo llama automáticamente cuando es necesario.

Para obtener información relacionada y `AfxDaoInit`un ejemplo de llamadas, consulte [nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="afxdaoterm"></a><a name="afxdaoterm"></a>AfxDaoTerm

Esta función finaliza el motor de base de datos DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Observaciones

Normalmente, solo es necesario llamar a esta función en un archivo DLL de MFC normal; una aplicación llamará `AfxDaoTerm` automáticamente cuando sea necesario.

En archivos DLL de `AfxDaoTerm` MFC `ExitInstance` normales, llame antes de la función, pero después de que se hayan destruido todos los objetos DAO de MFC.

Para obtener información relacionada, véase [la Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
