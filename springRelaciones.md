# SPRING BOOT - RELACIONES

NUEVOS ATRIBUTOS
OPCIONALES: SIRVEN PARA GESTION DE BASE DE DATOS
NO AGREGAR EN CONSTRUCTORES NI EN GETTER SETTER

    @Column(updatable = false) // INDICA QUQE NO VA A PODER SER ACTUALIZAR
    private Date createdAt; // guarda fecha cuando se inserta dato
    
    private Date updatedAt; // Guarda fecha cuando se actualiza dato
    // private Date deletedAt; // Fecha de eliminacion logica(cambio de estado, no borrar)

Relacion 1 a 1:
tabla con fk:    

    // LAZY: no trae tabla asociada solo cuando haga la solicitud
    // EAGER: trae tabla asociada enseguida
    
    @OneToOne(fetch=FetchType.LAZY)
    @JoinColumn(name="usuario_id") // FK con tabla relacionada
    private Usuario usuario;

E n la tabla asociada que no tiene fk:

    // Tabla Asociada sin fk.	Si se elimina algo, se elimina licencia
	@OneToOne(mappedBy="usuario", cascade=CascadeType.ALL, fetch=FetchType.LAZY)
	private Licencia licencia;
	

LUEGO DE GETTER & SETTER
INSERTAR EN BASE DE DATOS FECHA DE CREACION ANTES QUE REGISTRAR LA QUERY

    @PrePersist
    protected void onCreate(){
        this.createdAt = new Date();
    }
    @PreUpdate
    protected void onUpdate(){
        this.updatedAt = new Date();
}



    