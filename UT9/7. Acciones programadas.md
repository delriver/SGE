# Crear acciones programadas (Cronjobs)

Los cronjobs permiten programar acciones a realizar en los momentos que se asignen.



---

## Ejemplo Básico de Conexión

### Código de creación de Cronjob
El código debe incluirse en el xml de la vista del modelo, al igual que por ejemplo los actions.

~~~xml

<data noupdate="1">
    <record id="ir_cron_crear_facturas_recurrentes" model="ir.cron">
      <field name="name">Crear facturas recurrentes</field>
      <field name="model_id" ref="model_account_move"/>
      <field name="state">code</field>
      <field name="code">model._llamar_crear_factura()</field>
      <field name="interval_number">1</field>
      <field name="interval_type">days</field>
      <field name="nextcall" eval="(DateTime.now() + timedelta(days=1)).strftime('%Y-%m-%d 06:00:00')"/>
    </record>
</data>
~~~

### Explicación
1. **`record id`**: Id asignado al cronjob (Debe ser único)
2. **`name`**: Nombre del cronjob
3. **`model_id`**: Modelo sobre el que se ejecutará la acción
4. **`state`** y **`code`**: Método a ser llamado
5. **`interval_number`**: Número de veces que se va a llamar la acción programada
6. **`interval_type`**: Unidad de intervalo
7. **`nextcall`**: Cuando será la próxima llamada (En este caso a las 6 de la mañana del día siguiente)
---
