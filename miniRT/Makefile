# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: afrasch <afrasch@student.42heilbronn.de    +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2022/06/30 11:47:42 by arohmann          #+#    #+#              #
#    Updated: 2022/06/30 17:07:20 by afrasch          ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

NAME		= miniRT

CFLAGS		= -Wall -Wextra -Werror -O2

CC			= cc

SRC			:= main.c read_file.c read_utils.c read_elements.c \
				read_items.c read_objs.c read_objs_2.c light.c error.c \
				vec_math.c vec_math2.c window.c send_rays.c trace_rays.c \
				colors.c colors2.c find_t.c find_t2.c intersect.c multisample.c\

LDLIBS		:= -lft -lglfw -L "/Users/$(USER)/.brew/opt/glfw/lib/" -lMLX42

LIBDIRS		:= $(wildcard libs/*)

LDLIBS		:= $(addprefix -L./, $(LIBDIRS)) $(LDLIBS)

INCLUDES	:= -I./include/ $(addprefix -I./, $(addsuffix /include, $(LIBDIRS)))

SDIR		:= src

ODIR		:= obj

OBJS		:= $(addprefix $(ODIR)/, $(SRC:.c=.o))

RM			= rm -rf

all: $(NAME)

$(NAME): $(OBJS)
	make -C ./libs/libft/
	make -C ./libs/MLX42/
	$(CC) $(CFLAGS) -o $@ $(OBJS) $(LDLIBS)

$(ODIR)/%.o: $(SDIR)/%.c
	@mkdir -p $(ODIR)
	$(CC) $(CFLAGS) $(INCLUDES) -c $< -o $@

clean:
	make clean -C ./libs/libft/
	make clean -C ./libs/MLX42/
	$(RM) $(ODIR)

fclean: clean
	make fclean -C ./libs/libft/
	make fclean -C ./libs/MLX42/
	$(RM) $(NAME)

re: fclean $(NAME)

.PHONY: all clean fclean re
