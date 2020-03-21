---
title: 'Intercambio de campos de registros: Trabajar con el código de asistente'
ms.date: 05/09/2019
helpviewer_keywords:
- DoFieldExchange method, overriding
- Unicode, with database classes
- field data members, declaring
- RFX (ODBC), wizard code
- RFX (ODBC), implementing
- field data members
- ODBC, RFX
- m_nParams data member, initializing
- m_nFields data member
- m_nParams data member
- overriding, DoFieldExchange
- m_nFields data member, initializing
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
ms.openlocfilehash: 1149ab2b85c9cd803da0cd2d2ed6d931a020764e
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077081"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>Intercambio de campos de registros: Trabajar con el código de asistente

> [!NOTE]
> El Asistente para consumidores ODBC de MFC no está disponible en Visual Studio 2019 ni en versiones posteriores. Aun así, puede crear un consumidor de forma manual.

En este tema se explica el código que el Asistente para aplicaciones MFC y **Agregar clase** (como se describe en [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) escriben para admitir RFX y cómo se puede modificar este código.

> [!NOTE]
>  Este tema se aplica a clases derivadas de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usa la obtención masiva de filas, se implementará el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para comprender las diferencias, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Cuando cree una clase de conjunto de registros con el Asistente para aplicaciones MFC o **Agregar clase**, el asistente escribirá automáticamente los siguientes elementos relacionados con RFX, en función de las opciones de origen de datos, tabla y columna que seleccionó en el asistente:

- Declaraciones de los miembros de datos de campo del conjunto de registros en la clase de conjunto de registros.

- Una invalidación de `CRecordset::DoFieldExchange`.

- Una inicialización de los miembros de datos de campo del conjunto de registros en el constructor de clase del conjunto de registros.

##  <a name="field-data-member-declarations"></a><a name="_core_the_field_data_member_declarations"></a> Declaraciones de miembro de datos de campo

El asistente escribe una declaración de clase de conjunto de registros en un archivo .h que es similar a la siguiente para la clase `CSections`:

```cpp
class CSections : public CRecordset
{
public:
   CSections(CDatabase* pDatabase = NULL);
   DECLARE_DYNAMIC(CSections)

// Field/Param Data
   CString   m_strCourseID;
   CString   m_strInstructorID;
   CString   m_strRoomNo;
   CString   m_strSchedule;
   CString   m_strSectionNo;

// Overrides
   // Wizard generated virtual function overrides
   protected:
   virtual CString GetDefaultConnect();  // Default connection string
   virtual CString GetDefaultSQL();      // Default SQL for Recordset
   virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support

// Implementation
#ifdef _DEBUG
   virtual void AssertValid() const;
   virtual void Dump(CDumpContext& dc) const;
#endif

};
```

Si agrega miembros de datos de parámetros o nuevos miembros de datos de campo enlazados por usted mismo, debe incluirlos después de los generados por el asistente.

Además, tenga en cuenta que el asistente reemplaza la función miembro `DoFieldExchange` de la clase `CRecordset`.

##  <a name="dofieldexchange-override"></a><a name="_core_the_dofieldexchange_override"></a> Invalidación de DoFieldExchange

[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) es la esencia de RFX. El marco llama a `DoFieldExchange` cada vez que necesita mover datos del origen de datos al conjunto de registros o bien del conjunto de registros al origen de datos. `DoFieldExchange` también admite la obtención de información sobre los miembros de datos de campo a través de las funciones miembro [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) e [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).

La siguiente invalidación `DoFieldExchange` es para la clase `CSections`. El asistente escribe la función en el archivo .cpp para la clase de conjunto de registros.

```cpp
void CSections::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Text(pFX, "CourseID", m_strCourseID);
   RFX_Text(pFX, "InstructorID", m_strInstructorID);
   RFX_Text(pFX, "RoomNo", m_strRoomNo);
   RFX_Text(pFX, "Schedule", m_strSchedule);
   RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

Observe las siguientes características clave de la función:

- Esta sección de la función se denomina "asignación de campo".

- Una llamada a `CFieldExchange::SetFieldType`, mediante el puntero `pFX`. Esta llamada especifica que todas las llamadas de función RFX hasta el final de `DoFieldExchange` o la siguiente llamada a `SetFieldType` son columnas de salida. Para obtener más información, vea [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

- Varias llamadas a la función global `RFX_Text`, una por cada miembro de datos de campo (todas ellas variables `CString` en el ejemplo). Estas llamadas especifican la relación entre un nombre de columna en el origen de datos y un miembro de datos de campo. Las funciones de RFX llevan a cabo la transferencia de datos real. La biblioteca de clases proporciona funciones RFX para todos los tipos de datos comunes. Para obtener más información sobre las funciones de RFX, consulte [intercambio de campos de registros: usar las funciones de RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md).

    > [!NOTE]
    >  El orden de las columnas del conjunto de resultados debe coincidir con el orden de las llamadas de función RFX de `DoFieldExchange`.

- El puntero `pFX` a un objeto [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) que el marco pasa al llamar a `DoFieldExchange`. El objeto `CFieldExchange` especifica la operación que `DoFieldExchange` va a llevar a cabo, la dirección de la transferencia y otra información de contexto.

##  <a name="recordset-constructor"></a><a name="_core_the_recordset_constructor"></a> Constructor del conjunto de registros

El constructor del conjunto de registros que escriben los asistentes contiene dos elementos relacionados con RFX:

- Una inicialización para cada miembro de datos de campo.

- Una inicialización para el miembro de datos [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields), que contiene el número de miembros de datos de campo.

El constructor para el ejemplo del conjunto de registros `CSections` tiene este aspecto:

```cpp
CSections::CSections(CDatabase* pdb)
   : CRecordset(pdb)
{
   m_strCourseID = "";
   m_strInstructorID = "";
   m_strRoomNo = "";
   m_strSchedule = "";
   m_strSectionNo = "";
   m_nFields = 5;
}
```

> [!NOTE]
>  Si agrega miembros de datos de campo manualmente, como sucedería si enlaza nuevas columnas dinámicamente, debe incrementar `m_nFields`. Para hacerlo, agregue otra línea de código, como la siguiente:

```cpp
m_nFields += 3;
```

Este es el código para agregar tres nuevos campos. Si agrega miembros de datos de parámetros, debe inicializar el miembro de datos [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams), que contiene el número de miembros de datos de parámetros. Coloque la inicialización `m_nParams` fuera de los corchetes.

## <a name="see-also"></a>Consulte también

[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)