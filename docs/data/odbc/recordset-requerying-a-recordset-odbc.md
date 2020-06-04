---
title: 'Conjunto de registros: Volver a consultar un conjunto de registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
ms.openlocfilehash: cdae28f81eebe8427bc829072e0d9a83c6ec1722
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366945"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Conjunto de registros: Volver a consultar un conjunto de registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo puede usar un objeto de conjunto de registros para volver a consultar (es decir, actualizar) a sí mismo desde la base de datos y cuándo es posible que desee hacerlo con la [requery](../../mfc/reference/crecordset-class.md#requery) función miembro.

Las principales razones para volver a consultar un conjunto de registros son:

- Ponga el conjunto de registros actualizado con respecto a los registros agregados por usted o por otros usuarios y registros eliminados por otros usuarios (los que elimine ya se reflejan en el conjunto de registros).

- Actualice el conjunto de registros en función de los valores de parámetro sin cambios.

## <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>Poner al día el conjunto de registros

Con frecuencia, querrá volver a consultar el objeto de conjunto de registros para mantenerlo actualizado. En un entorno de base de datos multiusuario, otros usuarios pueden realizar cambios en los datos durante la vida del conjunto de registros. Para obtener más información sobre cuándo el conjunto de registros refleja los cambios realizados por otros usuarios y cuándo los conjuntos de registros de otros usuarios reflejan los cambios, vea Conjunto de registros: cómo los conjuntos de [registros actualizan registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) y [Dynaset](../../data/odbc/dynaset.md).

## <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>Consulta basada en nuevos parámetros

Otro uso frecuente —e igualmente importante— de [Requery](../../mfc/reference/crecordset-class.md#requery) es seleccionar un nuevo conjunto de registros basado en el cambio de valores de parámetro.

> [!TIP]
> La velocidad de consulta es `Requery` probablemente significativamente más rápida `Open` si llama con valores de parámetro cambiantes que si vuelve a llamar.

## <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>Consulta de Dynasets frente a instantáneas

Dado que los conjuntos de registros dinámicos están diseñados para presentar un conjunto de registros con datos dinámicos actualizados, desea volver a consultar los conjuntos de registros dinámicos con frecuencia si desea reflejar las adiciones de otros usuarios. Las instantáneas, por otro lado, son útiles porque puede confiar de forma segura en su contenido estático mientras prepara informes, calcula los totales, etc. Aún así, es posible que a veces también desee volver a consultar una instantánea. En un entorno multiusuario, los datos de instantánea pueden perder la sincronización con el origen de datos a medida que otros usuarios cambian la base de datos.

#### <a name="to-requery-a-recordset-object"></a>Para volver a consultar un objeto de conjunto de registros

1. Llame a la [Requery](../../mfc/reference/crecordset-class.md#requery) función miembro del objeto.

Como alternativa, puede cerrar y volver a abrir el conjunto de registros original. En cualquier caso, el nuevo conjunto de registros representa el estado actual del origen de datos.

Para obtener un ejemplo, vea Vistas de [registro: rellenar un cuadro de lista desde un segundo conjunto](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)de registros .

> [!TIP]
> Para `Requery` optimizar el rendimiento, evite cambiar el [filtro](../../data/odbc/recordset-filtering-records-odbc.md) u [ordenar](../../data/odbc/recordset-sorting-records-odbc.md)del conjunto de registros. Cambie solo el valor `Requery`del parámetro antes de llamar a .

Si `Requery` se produce un error en la llamada, puede volver a intentar la llamada; de lo contrario, la aplicación debe terminar correctamente. Una llamada `Requery` `Open` a o podría fallar por cualquiera de una serie de razones. Tal vez se produce un error de red; o, durante la llamada, después de que se liberen los datos existentes pero antes de que se obtengan los nuevos datos, otro usuario podría obtener acceso exclusivo; o la tabla de la que depende el conjunto de registros podría eliminarse.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Conjunto de registros: Crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
