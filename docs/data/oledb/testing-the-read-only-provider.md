---
title: "Probar el proveedor de s&#243;lo lectura | Microsoft Docs"
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
  - "proveedores OLE DB, llamar"
  - "proveedores OLE DB, pruebas"
  - "probar proveedores"
  - "pruebas, proveedores OLE DB"
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Probar el proveedor de s&#243;lo lectura
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para probar un proveedor, necesita un consumidor.  Será una ventaja que el consumidor se corresponda con el proveedor.  Las plantillas de consumidor OLE DB son un contenedor delgado de OLE DB que se corresponden con los objetos COM del proveedor.  Como el código fuente se distribuye con las plantillas de consumidor, es fácil utilizarlas para depurar un proveedor.  Las plantillas de consumidor también representan una forma muy reducida y rápida de desarrollar aplicaciones para consumidores.  
  
 En el ejemplo de este tema se crea una aplicación predeterminada del Asistente para aplicaciones MFC para un consumidor de prueba.  La aplicación de prueba es un cuadro de diálogo sencillo con el código de una plantilla de consumidor OLE DB agregado.  
  
### Para crear la aplicación de prueba  
  
1.  En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En el panel Tipos de proyecto, seleccione la carpeta **Proyectos de Visual C\+\+**.  En el panel Plantillas, seleccione **Aplicación MFC**.  
  
3.  Como nombre de proyecto, escriba **TestProv** y haga clic en **Aceptar**.  
  
     Aparece el Asistente para aplicaciones MFC.  
  
4.  En la página **Tipo de aplicación**, active **Basada en cuadros de diálogo**.  
  
5.  En la página **Características avanzadas**, seleccione **Automatización** y, a continuación, haga clic en **Finalizar**.  
  
> [!NOTE]
>  La aplicación no requiere compatibilidad con la Automatización si agrega **CoInitialize** en **CTestProvApp::InitInstance**.  
  
 Puede ver y editar el cuadro de diálogo TestProv \(IDD\_TESTPROV\_DIALOG\) seleccionándolo en la Vista de recursos.  Coloque dos cuadros de lista en el cuadro de diálogo, uno para cada cadena del conjunto de filas.  Desactive la propiedad Sort para los dos cuadros de lista; para ello, presione ALT\+Entrar con un cuadro de lista seleccionado, haga clic en la ficha **Estilos** y desactive la casilla **Ordenar**.  Coloque también un botón **Ejecutar** en el cuadro de diálogo para buscar el archivo.  El cuadro de diálogo finalizado de TestProv debe tener dos cuadros de lista con las etiquetas "String 1" y "String 2", respectivamente; también tiene botones **Aceptar**, **Cancelar** y **Ejecutar**.  
  
 Abra el archivo de encabezado para la clase de cuadro de diálogo \(en este caso, TestProvDlg.h\).  Agregue las siguientes líneas de código al archivo de encabezado \(fuera de las declaraciones de clase\):  
  
```  
////////////////////////////////////////////////////////////////////////  
// TestProvDlg.h  
  
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
  
 El código representa un registro de usuario que define las columnas que deben estar en el conjunto de filas.  Cuando el cliente llama a **IAccessor::CreateAccessor**, utiliza estas entradas para especificar las columnas que hay que enlazar.  Las plantillas de consumidor de OLE DB también permiten enlazar columnas dinámicamente.  Las macros COLUMN\_ENTRY son la versión para el cliente de las macros PROVIDER\_COLUMN\_ENTRY.  Las dos macros COLUMN\_ENTRY especifican el ordinal, el tipo, la longitud y el miembro de datos para las dos cadenas.  
  
 Agregue una función controladora para el botón **Ejecutar**; para ello, presione CTRL y haga doble clic en el botón **Ejecutar**.  Coloque las siguientes líneas de código en la función:  
  
```  
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
void CtestProvDlg::OnRun()  
{  
   CCommand<CAccessor<CProvider> > table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
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
  
 Las clases `CCommand`, `CDataSource` y `CSession` pertenecen a las plantillas de consumidor de OLE DB.  Cada clase emula un objeto COM en el proveedor.  El objeto `CCommand` utiliza la clase `CProvider`, declarada en el archivo de encabezado, como un parámetro de plantilla.  El parámetro `CProvider` representa enlaces que utiliza para tener acceso a los datos desde el proveedor.  A continuación se muestra el código de `Open` para el origen de datos, la sesión, y el comando:  
  
```  
if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
   return;  
  
if (session.Open(source) != S_OK)  
   return;  
  
if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
   return;  
```  
  
 Las líneas para abrir cada una de las clases crean cada objeto COM en el proveedor.  Para buscar el proveedor, utilice su ProgID.  Puede obtener el ProgID en el Registro del sistema o buscar en el archivo MyProvider.rgs \(abra el directorio del proveedor y busque la clave ProgID\).  
  
 El archivo MyData.txt se incluye en el ejemplo MyProv.  Para crear un archivo propio, utilice un editor y escriba un número par de cadenas, presionando ENTRAR después de escribir cada cadena.  Si mueve el archivo, cambie el nombre de la ruta de acceso.  
  
 Pase la cadena "c:\\\\samples\\\\myprov\\\\MyData.txt" en la línea `table.Open`.  Si recorre paso a paso la llamada `Open`, puede ver que se pasa esta cadena al método `SetCommandText` del proveedor.  Tenga en cuenta que el método `ICommandText::Execute` utilizó esa cadena.  
  
 Para obtener los datos, llame a `MoveNext` en la tabla.  `MoveNext` llama a las funciones **IRowset::GetNextRows**, `GetRowCount` y `GetData`.  Cuando no queden filas \(es decir, cuando la posición actual del conjunto de filas sea mayor que `GetRowCount`\), finalizará el bucle:  
  
```  
while (table.MoveNext() == S_OK)  
{  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
 Tenga en cuenta que cuando no queden filas, los proveedores devolverán **DB\_S\_ENDOFROWSET**.  El valor de **DB\_S\_ENDOFROWSET** no es un error.  Debe comprobar siempre el valor de `S_OK` para cancelar un bucle de búsqueda de datos y no utilizar la macro SUCCEEDED.  
  
 Ahora podrá compilar y probar el programa.  
  
## Vea también  
 [Mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)