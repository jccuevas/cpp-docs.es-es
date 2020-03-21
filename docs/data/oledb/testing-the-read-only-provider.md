---
title: Probar el proveedor de sólo lectura
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
ms.openlocfilehash: a173e1466179dfb40a33d7bdb4a94eabdbf23cc0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079059"
---
# <a name="testing-the-read-only-provider"></a>Probar el proveedor de sólo lectura

Para probar un proveedor, necesita un consumidor. Ayuda si el consumidor puede hacer coincidir con el proveedor. Las plantillas de consumidor OLE DB son un contenedor fino alrededor de OLE DB y que coinciden con los objetos COM del proveedor. Dado que el origen se incluye con las plantillas de consumidor, es fácil depurar con ellos un proveedor. Las plantillas de consumidor son también una manera muy pequeña y rápida de desarrollar aplicaciones de consumidor.

En el ejemplo de este tema se crea una aplicación del Asistente para aplicaciones MFC predeterminada para un consumidor de prueba. La aplicación de prueba es un cuadro de diálogo simple con OLE DB código de plantilla de consumidor agregado.

## <a name="to-create-the-test-application"></a>Para crear la aplicación de prueba

1. En el menú **Archivo**, haga clic en **Nuevo** y, después, en **Proyecto**.

1. En el panel **tipos de proyecto** , seleccione la carpeta **instalado** > **Visual C++**  > **MFC/ATL** . En el panel **plantillas** , seleccione **aplicación MFC**.

1. En el nombre del proyecto, escriba *TestProv*y, a continuación, haga clic en **Aceptar**.

   Aparece el Asistente para **aplicaciones MFC** .

1. En la página **tipo de aplicación** , seleccione **basado en cuadros de diálogo**.

1. En la página **características avanzadas** , seleccione **automatización**y, a continuación, haga clic en **Finalizar**.

> [!NOTE]
> La aplicación no requiere compatibilidad con automatización si agrega `CoInitialize` en `CTestProvApp::InitInstance`.

Puede ver y editar el cuadro de diálogo **TestProv** (IDD_TESTPROV_DIALOG) seleccionándolo en **vista de recursos**. Coloque dos cuadros de lista, uno para cada cadena del conjunto de filas, en el cuadro de diálogo. Para desactivar la propiedad de ordenación de ambos cuadros de lista, presione **Alt**+**entrar** cuando se selecciona un cuadro de lista y establezca la propiedad **Sort** en **false**. Además, coloque un botón **Ejecutar** en el cuadro de diálogo para capturar el archivo. El cuadro de diálogo **TestProv** finalizado debe tener dos cuadros de lista con la etiqueta "cadena 1" y "cadena 2", respectivamente; también tiene botones **Aceptar**, **Cancelar**y **Ejecutar** .

Abra el archivo de encabezado para la clase de cuadro de diálogo (en este caso, TestProvDlg. h). Agregue el código siguiente al archivo de encabezado (fuera de las declaraciones de clase):

```cpp
////////////////////////////////////////////////////////////////////////
// TestProvDlg.h
#include <atldbcli.h>  

class CProvider
{
// Attributes
public:
   char   szField1[16];
   char   szField2[16];

   // Binding Maps
BEGIN_COLUMN_MAP(CProvider)
   COLUMN_ENTRY(1, szField1)
   COLUMN_ENTRY(2, szField2)
END_COLUMN_MAP()
};
```

El código representa un registro de usuario que define qué columnas se incluirán en el conjunto de filas. Cuando el cliente llama a `IAccessor::CreateAccessor`, utiliza estas entradas para especificar las columnas que se van a enlazar. Las plantillas de consumidor de OLE DB también permiten enlazar columnas dinámicamente. Las macros COLUMN_ENTRY son la versión del lado cliente de las macros de PROVIDER_COLUMN_ENTRY. Las dos macros COLUMN_ENTRY especifican el ordinal, el tipo, la longitud y el miembro de datos de las dos cadenas.

Para agregar una función de controlador para el botón **Ejecutar** , presione **Ctrl** y haga doble clic en el botón **Ejecutar** . Coloque el código siguiente en la función:

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession session;

   if (source.Open("Custom.Custom.1", NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)
      return;

   while (table.MoveNext() == S_OK)
   {
      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
   }
}
```

Todas las clases `CCommand`, `CDataSource`y `CSession` pertenecen a las plantillas de consumidor de OLE DB. Cada clase imita un objeto COM en el proveedor. El objeto `CCommand` toma la clase `CProvider`, declarada en el archivo de encabezado, como un parámetro de plantilla. El parámetro `CProvider` representa los enlaces que se utilizan para tener acceso a los datos del proveedor.

Las líneas para abrir cada una de las clases crean cada objeto COM en el proveedor. Para buscar el proveedor, utilice el `ProgID` del proveedor. Puede obtener el `ProgID` del registro del sistema o si busca en el archivo. RGS personalizado (Abra el directorio del proveedor y busque la clave `ProgID`).

El archivo de datos. txt se incluye con el ejemplo `MyProv`. Para crear un archivo propio, use un editor y escriba un número par de cadenas y presione **entrar** entre cada cadena. Cambie el nombre de la ruta de acceso si mueve el archivo.

Pase la cadena "c:\\\Samples\\\myprov\\\MyData.txt" en la línea de `table.Open`. Si va a la llamada `Open`, verá que esta cadena se pasa al método `SetCommandText` en el proveedor. Tenga en cuenta que el método `ICommandText::Execute` utilizó esa cadena.

Para capturar los datos, llame a `MoveNext` en la tabla. `MoveNext` llama a las funciones `IRowset::GetNextRows`, `GetRowCount`y `GetData`. Cuando no hay más filas (es decir, la posición actual en el conjunto de filas es mayor que `GetRowCount`), el bucle finaliza.

Cuando no hay más filas, los proveedores devuelven DB_S_ENDOFROWSET. El valor DB_S_ENDOFROWSET no es un error. Siempre debe comprobar en S_OK para cancelar un bucle de búsqueda de datos y no utilizar la macro SUCCEEDED.

Ahora debería poder compilar y probar el programa.

## <a name="see-also"></a>Consulte también

[Mejorar un proveedor sencillo de solo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)