---
title: 'Conjunto de registros: Volver a consultar un conjunto de registros (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1445273d29fc521b24fbf04ffc5abec1fadd4e59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Conjunto de registros: Volver a consultar un conjunto de registros (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 Este tema explica cómo puede usar un objeto de conjunto de registros para volver a consultar (es decir, actualizar) propio de la base de datos y cuándo puede resultar conveniente hacerlo con el [Requery](../../mfc/reference/crecordset-class.md#requery) función miembro.  
  
 Las razones principales para volver a consultar un conjunto de registros son:  
  
-   Ponga el conjunto de registros al día con respecto a los registros agregados por el usuario o por otros usuarios y los registros eliminados por otros usuarios (los que elimine ya aparecen reflejados en el conjunto de registros).  
  
-   Actualizar el conjunto de registros basándose en los valores de parámetros de variables.  
  
##  <a name="_core_bringing_the_recordset_up_to_date"></a>Volver a poner el conjunto de registros de seguridad hasta la fecha  
 Con frecuencia, deberá volver a consultar el objeto de conjunto de registros para ponerla al día. En un entorno de base de datos multiusuario, otros usuarios pueden realizar cambios a los datos durante la vida del conjunto de registros. Para obtener más información acerca de si el conjunto de registros refleja los cambios realizados por otros usuarios y cuando los conjuntos de registros de otros usuarios reflejan los cambios, consulte [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) y [Dynaset](../../data/odbc/dynaset.md).  
  
##  <a name="_core_requerying_based_on_new_parameters"></a>Volver a consultar basada en nuevos parámetros  
 Otro uso frecuente e igualmente importante: el uso de [Requery](../../mfc/reference/crecordset-class.md#requery) consiste en seleccionar un nuevo conjunto de registros basados en valores de parámetro diferentes.  
  
> [!TIP]
>  Velocidad de consulta es probablemente mucho más rápida si se llama a **Requery** con el cambio de valores de parámetro que si se llama a **abiertos** nuevo.  
  
##  <a name="_core_requerying_dynasets_vs.._snapshots"></a>Volver a consultar conjuntos de registros dinámicos vs. Instantáneas  
 Como conjuntos de registros dinámicos están diseñados para mostrar un conjunto de registros con datos dinámicos y actualizados, es conveniente volver a consultar conjuntos de registros dinámicos a menudo si desea reflejar las adiciones de otros usuarios. Las instantáneas, por otro lado, son útiles porque se puede confiar en su contenido estático mientras preparar informes, calcular totales y así sucesivamente. No obstante, a veces puede volver a consultar también una instantánea. En un entorno multiusuario, datos de la instantánea podrían perder la sincronización con el origen de datos como otros usuarios modifican la base de datos.  
  
#### <a name="to-requery-a-recordset-object"></a>Para volver a consultar un objeto de conjunto de registros  
  
1.  Llame a la [Requery](../../mfc/reference/crecordset-class.md#requery) función de miembro del objeto.  
  
 Como alternativa, puede cerrar y volver a abrir el conjunto de registros original. En cualquier caso, el nuevo conjunto de registros representa el estado actual del origen de datos.  
  
 Para obtener un ejemplo, vea [vistas de registros: llenar un cuadro de lista de otro conjunto de registros](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
> [!TIP]
>  Para optimizar el **Requery** rendimiento, evite cambiar el conjunto de registros [filtro](../../data/odbc/recordset-filtering-records-odbc.md) o [ordenación](../../data/odbc/recordset-sorting-records-odbc.md). Cambiar solo el valor del parámetro antes de llamar a **Requery**.  
  
 Si el **Requery** llamar a un error, puede volver a intentar la llamada; de lo contrario, se cerrará la aplicación. Una llamada a **Requery** o **abiertos** puede provocar errores en cualquiera de una serie de motivos. Quizás se produce un error de red; o bien, durante la llamada, después del lanzamiento de los datos existentes, pero antes de que se obtienen los nuevos datos, otro usuario podría obtener acceso exclusivo; o bien, se pudo eliminar la tabla de la que depende el conjunto de registros.  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [Conjunto de registros: Crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)