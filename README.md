# -*- coding: utf-8 -*-
import vk_api


def main():
    TOKEN = "9efd0295084cac34964ca3e44589f70353e29f36072a0d49ef843ec07e572c1b4a87cf9da1631975e4a59"
    vk_session = vk_api.VkApi(token=token)

    try:
        vk_session.auth(token_only=True)
    except vk_api.AuthError as error_msg:
        print(error_msg)
        return

    upload = vk_api.VkUpload(vk_session)

    photo = upload.photo(  # Подставьте свои данные
        '/root/3301.jpg',
        album_id=200851098,
        group_id=74030368
    )

    vk_photo_url = 'https://vk.com/photo{}_{}'.format(
        photo[0]['owner_id'], photo[0]['id']
    )

    print(photo, '\nLink: ', vk_photo_url)


if __name__ == '__main__':
    main()
