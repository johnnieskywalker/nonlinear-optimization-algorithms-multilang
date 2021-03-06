# =============================================================================
# nlp-unconstrained-core/hooke-jeeves/go/src/Makefile
# =============================================================================
# Nonlinear Optimization Algorithms Multilang. Version 0.1
# =============================================================================
# Nonlinear programming algorithms as the (un-)constrained minimization
# problems with the focus on their numerical expression using various
# programming languages.
#
# This is the Hooke and Jeeves nonlinear unconstrained minimization algorithm.
# =============================================================================

EXEC1   = hooke
EXEC2S  = -woods
EXEC2   = $(EXEC1)$(EXEC2S)
DEPS1S  = rosenbrock
DEPS1   = $(EXEC1).o $(DEPS1S).o
DEPS2S  = woods
DEPS2   = $(EXEC2).o $(DEPS2S)$(EXEC2S).o
BIN_DIR = ../bin
OBJ_DIR = ../obj

# Specify flags and other vars here.
CC      = go tool
CFLAGS  = compile -complete -o
LDFLAGS = link -o

MV      = mv
MVFLAGS = -v

# Making the first target (rosenbrock).
$(DEPS1): %.o: %.go
	$(if $(findstring $(EXEC1),$@),$(info )$(info === Making the FIRST \
	target (rosenbrock) ======================================))

	$(CC) $(CFLAGS) $@ $< $(if $(findstring $(EXEC1),$<),,$(EXEC1).go)

$(EXEC1): $(DEPS1)
	$(CC) $(LDFLAGS) $(EXEC1) $(DEPS1S).o

# Making the second target (woods).
$(DEPS2): %$(EXEC2S).o: %.go
	$(if $(findstring $(EXEC2),$@),$(info )$(info === Making the SECOND \
	target (woods) ==========================================))

	$(CC) $(CFLAGS) $@ $< $(if $(findstring $(EXEC1),$<),,$(EXEC1).go)

$(EXEC2): $(DEPS2)
	$(CC) $(LDFLAGS) $(EXEC2) $(DEPS2S)$(EXEC2S).o

.PHONY: rosenbrock woods all clean

rosenbrock: $(EXEC1)

woods: $(EXEC2)

all: rosenbrock woods
	$(MV) $(MVFLAGS) $(EXEC1) $(EXEC2) $(BIN_DIR)
	$(MV) $(MVFLAGS) $(DEPS1) $(DEPS2) $(OBJ_DIR)

clean:
	$(RM) $(EXEC1) $(DEPS1) $(EXEC2) $(DEPS2)

# =============================================================================
# vim:set nu:et:ts=4:sw=4:
# =============================================================================
