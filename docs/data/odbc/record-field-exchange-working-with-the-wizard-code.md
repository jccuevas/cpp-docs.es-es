---
title: "Intercambio de campos de registros: Trabajar con el c&#243;digo de asistente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DoFieldExchange (método), reemplazar"
  - "miembros de datos de campo"
  - "miembros de datos de campo, declarar"
  - "m_nFields (miembro de datos)"
  - "m_nFields (miembro de datos), inicializar"
  - "m_nParams (miembro de datos)"
  - "m_nParams (miembro de datos), inicializar"
  - "ODBC, RFX"
  - "reemplazar, DoFieldExchange"
  - "RFX (ODBC), implementar"
  - "RFX (ODBC), código de asistente"
  - "Unicode, con clases de base de datos"
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Intercambio de campos de registros: Trabajar con el c&#243;digo de asistente
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema explica el código que generan el Asistente para aplicaciones MFC y el comando **Agregar clase** \(como se describe en [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)\) para la compatibilidad con RFX y cómo puede resultar conveniente modificar ese código.  
  
> [!NOTE]
>  Este tema se aplica a clases derivadas de `CRecordset` donde no se haya implementado la obtención masiva de filas.  Si usa esta obtención masiva, se implementará el intercambio masivo de campos de registros \(RFX masivo\).  RFX masivo es similar a RFX.  Para comprender mejor estas diferencias, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Al crear una clase de conjunto de registros mediante el Asistente para aplicaciones MFC o el comando **Agregar clase**, el asistente escribe los siguientes elementos \(relacionados con RFX\) por usted, basándose en las opciones seleccionadas para origen de datos, tablas y columnas en el asistente:  
  
-   Declaraciones de los miembros de datos de campo del conjunto de registros en la clase de conjunto de registros  
  
-   Una función de reemplazo de `CRecordset::DoFieldExchange`  
  
-   Código de inicialización de los miembros de datos de campo en el constructor de la clase de conjunto de registros  
  
##  <a name="_core_the_field_data_member_declarations"></a> Declaraciones de los miembros de datos de campo  
 El asistente escribe una declaración de la clase de conjunto de registros en un archivo .h similar a los siguientes para la clase `CSections`:  
  
```  
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
  
 Si agrega miembros de datos de parámetro o nuevos miembros de datos de campo y los enlaza manualmente, agréguelos a continuación de los generados por el asistente.  
  
 Asimismo, observe que el asistente reemplaza la función miembro `DoFieldExchange` de la clase `CRecordset`.  
  
##  <a name="_core_the_dofieldexchange_override"></a> Función de reemplazo para DoFieldExchange  
 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) representa la esencia de RFX.  El marco de trabajo llama a `DoFieldExchange` cada vez que necesita mover datos desde el origen de datos al conjunto de registros o viceversa.  `DoFieldExchange` también permite obtener información sobre miembros de datos de campo a través de las funciones miembro [IsFieldDirty](../Topic/CRecordset::IsFieldDirty.md) e [IsFieldNull](../Topic/CRecordset::IsFieldNull.md).  
  
 La siguiente función de reemplazo para `DoFieldExchange` corresponde a la clase `CSections`.  El asistente escribe la función en el archivo .cpp para la clase de conjunto de registros.  
  
```  
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
  
-   Esta sección de la función se denomina asignación de campos.  
  
-   Una llamada a `CFieldExchange::SetFieldType`, a través del puntero `pFX`.  Esta llamada especifica que todas las llamadas a la función RFX hasta el final de `DoFieldExchange` o la siguiente llamada a `SetFieldType` se consideran columnas de resultados.  Para obtener más información, vea [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md).  
  
-   Varias llamadas a la función global `RFX_Text`, una por cada miembro de datos de campo \(todas las cuales son variables `CString` en el ejemplo\).  Estas llamadas especifican la relación entre un nombre de columna del origen de datos y un miembro de datos de campo.  Las funciones RFX realizan la transferencia de datos real.  La biblioteca de clases proporciona funciones RFX para todos los tipos de datos comunes.  Para obtener más información sobre las funciones RFX, vea [Intercambio de campos de registros: Utilizar las funciones de RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md).  
  
    > [!NOTE]
    >  El orden de las columnas en el conjunto de resultados debe coincidir con el de las llamadas a la función RFX en `DoFieldExchange`.  
  
-   El puntero `pFX` a un objeto [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) que pasa el marco de trabajo al llamar a `DoFieldExchange`.  El objeto `CFieldExchange` especifica la operación que debe realizar `DoFieldExchange`, la dirección de la transferencia y otra información de contexto.  
  
##  <a name="_core_the_recordset_constructor"></a> Constructor de conjunto de registros  
 El constructor del conjunto de registros que generan los asistentes contiene dos elementos relacionados con RFX:  
  
-   Una inicialización para cada miembro de datos de campo  
  
-   Una inicialización para el miembro de datos [m\_nFields](../Topic/CRecordset::m_nFields.md), que contiene el número de miembros de datos de campo  
  
 El constructor del ejemplo de conjunto de registros `CSections` tiene este aspecto:  
  
```  
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
>  Si agrega miembros de datos de campo manualmente, como podría hacerlo al enlazar nuevas columnas dinámicamente, debe incrementar `m_nFields`.  Puede hacerlo anexando otra línea de código, como:  
  
```  
m_nFields += 3;  
```  
  
 Éste es el código para agregar tres nuevos campos.  Si agrega nuevos miembros de datos de parámetro, debe inicializar el miembro de datos [m\_nParams](../Topic/CRecordset::m_nParams.md), que contiene el número de miembros de datos de parámetro.  Coloque el código de inicialización de `m_nParams` fuera de los paréntesis.  
  
## Vea también  
 [Intercambio de campos de registros \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)