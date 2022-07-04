# SPRING BOOT - RELACIONES

// RELACION ONE TO ONE con usario

    EN MODELO LICENCIA
	@OneToOne(fetch=FetchType.LAZY)
	@JoinColumn(name="usuario_id") // FK de tabla relacionada
	private Usuario usuario;

    EN USUARIO
    // RELACION ONE TO ONE con licencia
	@OneToOne(mappedBy="usuario", cascade=CascadeType.ALL, fetch=FetchType.LAZY)
	private Licencia licencia;


//ManyToMany con roles

    EN MODELO USUARIO
	@ManyToMany(fetch = FetchType.EAGER)
	@JoinTable(
			name="roles_usuarios",							// nombre tabla relacional
			joinColumns = @JoinColumn(name="usuario_id"), nullable = false),	// columna entidad local
			inverseJoinColumns = @JoinColumn(name="rol_id", nullable = false)	// columna entidad externa
			)
	private List<Dispositivo> listaDispositivos;

    EN MODELO ROL / DISPOSITIVO
 	@ManyToMany(mappedBy = "roles", cascade = CascadeType.ALL,fetch = FetchType.LAZY)
	private List<Usuario> usuarios;


//MANY TO ONE - AUTO

	@ManyToOne(fetch = FetchType.LAZY)
	@JoinColumn(name="auto_id", nullable = false)
	private Auto auto;

    @OneToMany