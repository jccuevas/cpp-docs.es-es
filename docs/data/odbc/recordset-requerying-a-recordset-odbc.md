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
ms.openlocfilehash: b7cf40ca3b0c8e415368772063aee61008a52764
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212789"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Conjunto de registros: Volver a consultar un conjunto de registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo se puede usar un objeto de conjunto de registros para realizar una nueva consulta (es decir, actualizar) en la base de datos y Cuándo es posible que desee hacerlo con la función miembro [Requery](../../mfc/reference/crecordset-class.md#requery) .

Las principales razones para reconsultar un conjunto de registros son:

- Poner el conjunto de registros actualizado con respecto a los registros agregados por usted o por otros usuarios y registros eliminados por otros usuarios (los que elimine ya están reflejados en el conjunto de registros).

- Actualice el conjunto de registros basándose en el cambio de valores de parámetro.

##  <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>Actualizar el conjunto de registros

Con frecuencia, querrá consultar el objeto de conjunto de registros para ponerlo al día. En un entorno de base de datos multiusuario, otros usuarios pueden realizar cambios en los datos durante la vida del conjunto de registros. Para obtener más información sobre el momento en que el conjunto de registros refleja los cambios realizados por otros usuarios y cuando los conjuntos de registros de otros usuarios reflejan los cambios, vea conjunto de registros [: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) y [Dynaset](../../data/odbc/dynaset.md)de los conjuntos de registros.

##  <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>Nueva consulta basada en nuevos parámetros

Otro frecuente (y igualmente importante): el uso de [Requery](../../mfc/reference/crecordset-class.md#requery) es seleccionar un nuevo conjunto de registros en función de los valores de los parámetros.

> [!TIP]
>  La velocidad de consulta probablemente es significativamente más rápida si se llama a `Requery` con valores de parámetro variables que si se llama de nuevo a `Open`.

##  <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>Reconsultando conjuntos de registros dinámicos frente a instantáneas

Dado que los dynasets están diseñados para presentar un conjunto de registros con datos actualizados dinámicos, se recomienda reconsultar los conjuntos de registros dinámicos a menudo si desea reflejar las adiciones de otros usuarios. Por otro lado, las instantáneas son útiles porque puede confiar de forma segura en su contenido estático mientras prepara los informes, calcula los totales, etc. Aun así, en ocasiones podría querer también reconsultar una instantánea. En un entorno multiusuario, los datos de instantánea podrían perder la sincronización con el origen de datos a medida que otros usuarios cambien la base de datos.

#### <a name="to-requery-a-recordset-object"></a>Para reconsultar un objeto de conjunto de registros

1. Llame a la función miembro [Requery](../../mfc/reference/crecordset-class.md#requery) del objeto.

Como alternativa, puede cerrar y volver a abrir el conjunto de registros original. En cualquier caso, el nuevo conjunto de registros representa el estado actual del origen de datos.

Para obtener un ejemplo, vea [vistas de registros: llenar un cuadro de lista de un segundo conjunto de registros](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

> [!TIP]
>  Para optimizar el rendimiento de `Requery`, evite cambiar el [filtro](../../data/odbc/recordset-filtering-records-odbc.md) o la [ordenación](../../data/odbc/recordset-sorting-records-odbc.md)del conjunto de registros. Cambie solo el valor del parámetro antes de llamar a `Requery`.

Si se produce un error en la llamada `Requery`, puede reintentar la llamada; de lo contrario, la aplicación debe finalizar correctamente. Se puede producir un error en una llamada a `Requery` o `Open` por una serie de motivos. Es posible que se produzca un error de red; o bien, durante la llamada, una vez que se liberan los datos existentes, pero antes de que se obtengan los nuevos datos, otro usuario puede obtener acceso exclusivo. o bien, se puede eliminar la tabla de la que depende el conjunto de registros.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Conjunto de registros: Crear y cerrar conjuntos de registros (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
