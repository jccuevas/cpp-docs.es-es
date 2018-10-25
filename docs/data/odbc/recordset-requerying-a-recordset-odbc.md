---
title: 'Conjunto de registros: Volver a consultar un conjunto de registros (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7d228fb97cad2fba426aa6415564d3b7f60363b5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062689"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Conjunto de registros: Volver a consultar un conjunto de registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo puede usar un objeto de conjunto de registros a consultar (es decir, actualizar) propio de la base de datos y cuándo puede resultar conveniente hacerlo con el [Requery](../../mfc/reference/crecordset-class.md#requery) función miembro.

Las principales razones para volver a consultar un conjunto de registros son:

- Ponga el conjunto de registros al día con respecto a los registros agregados por ud. o por otros usuarios y los registros eliminados por otros usuarios (los que elimine ya aparecen reflejados en el conjunto de registros).

- Actualizar el conjunto de registros en función de cómo cambiar los valores de parámetro.

##  <a name="_core_bringing_the_recordset_up_to_date"></a> Poner el vertical del conjunto de registros hasta la fecha

Con frecuencia, deseará volver a consultar el objeto de conjunto de registros para ponerlo al día. En un entorno de base de datos multiusuario, otros usuarios pueden realizar cambios a los datos durante la vida del conjunto de registros. Para obtener más información acerca de cuándo el conjunto de registros refleja los cambios realizados por otros usuarios y cuando los conjuntos de registros de otros usuarios reflejan los cambios, consulte [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) y [Dynaset](../../data/odbc/dynaset.md).

##  <a name="_core_requerying_based_on_new_parameters"></a> Volver a consultar según los nuevos parámetros

Otro uso frecuente y es igualmente importante, el uso de [Requery](../../mfc/reference/crecordset-class.md#requery) consiste en seleccionar un nuevo conjunto de registros en función de cómo cambiar los valores de parámetro.

> [!TIP]
>  Velocidad de consulta es probablemente mucho más rápida si se llama a `Requery` con el cambio de los valores de parámetro que si se llama `Open` nuevo.

##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> Volver a consultar conjuntos de registros dinámicos vs. Instantáneas

Como conjuntos de registros dinámicos están diseñados para presentar un conjunto de registros con datos dinámicos y actualizados, es conveniente volver a consultar conjuntos de registros dinámicos a menudo si quiere reflejar las adiciones de otros usuarios. Las instantáneas, por otro lado, son útiles porque se puede confiar en su contenido estático mientras preparar informes, calcular totales y así sucesivamente. Aun así, en ocasiones, puede volver a consultar una instantánea también. En un entorno multiusuario, datos de instantáneas podrían perder la sincronización con el origen de datos a medida que otros usuarios cambian la base de datos.

#### <a name="to-requery-a-recordset-object"></a>Para volver a consultar un objeto de conjunto de registros

1. Llame a la [Requery](../../mfc/reference/crecordset-class.md#requery) función de miembro del objeto.

Como alternativa, puede cerrar y volver a abrir el conjunto de registros original. En cualquier caso, el nuevo conjunto de registros representa el estado actual del origen de datos.

Para obtener un ejemplo, vea [vistas de registros: llenar un cuadro de lista de otro conjunto de registros](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

> [!TIP]
>  Para optimizar `Requery` rendimiento, evite cambiar el conjunto de registros [filtro](../../data/odbc/recordset-filtering-records-odbc.md) o [ordenación](../../data/odbc/recordset-sorting-records-odbc.md). Cambiar solo el valor del parámetro antes de llamar a `Requery`.

Si el `Requery` llamar a un error, puede volver a intentar la llamada; de lo contrario, se cerrará la aplicación. Una llamada a `Requery` o `Open` pueden provocar errores en cualquiera de una serie de motivos. Quizás se produce un error de red; o bien, durante la llamada, tras el lanzamiento de los datos existentes, pero antes de que se obtengan los nuevos datos, otro usuario podría obtener acceso exclusivo; o bien, se puede eliminar la tabla del que depende el conjunto de registros.

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Conjunto de registros: Crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)